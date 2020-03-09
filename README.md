# CVE-2020-2555
Weblogic com.tangosol.util.extractor.ReflectionExtractor RCE

com.supeream.CVE_2020_2555

```
/*
 * author:Y4er.com
 *
 * gadget:
 *      BadAttributeValueExpException.readObject()
 *          com.tangosol.util.filter.LimitFilter.toString()
 *              com.tangosol.util.extractor.ChainedExtractor.extract()
 *                  com.tangosol.util.extractor.ReflectionExtractor.extract()
 *                      Method.invoke()
 *                      ...
 *                      Runtime.getRuntime.exec()
 */
 ```

 # Require
 This only works in JDK 8u76 and WITHOUT a security manager, because of `BadAttributeValueExpException` in here:
 https://github.com/JetBrains/jdk8u_jdk/commit/af2361ee2878302012214299036b3a8b4ed36974#diff-f89b1641c408b60efe29ee513b3d22ffR70
 And Please replace `coherence.jar` with your weblogic version, if not, you will get serialVersionUID inconsistent error.

 Only test on Centos jdk8u202 Weblogic 12.2.1.4.

![](https://user-images.githubusercontent.com/40487319/76184916-a6727200-6208-11ea-927a-938009ad54c1.gif)


 # Reference
 1. https://www.thezdi.com/blog/2020/3/5/cve-2020-2555-rce-through-a-deserialization-bug-in-oracles-weblogic-server
 2. https://www.youtube.com/watch?v=VzmZTYbm4Zw
 3. https://github.com/5up3rc/weblogic_cmd/