## Webpack Hash Test

[对Webpack的hash稳定性的初步探索](https://zhuanlan.zhihu.com/p/35093098?utm_source=wechat_session&utm_medium=social&utm_oi=27045073518592)

上文中，作者在webpack(4.3.0)下，分析了webpack的hash稳定性问题，并最终通过`HashedModuleIdsPlugin`解决了问题，详见[webpack/4.3.0](https://github.com/hushicai/webpack-hash-test/tree/webpack/4.3.0)分支。

我用最新版webpack(4.29.6)测试了一下，发现新版似乎已经解决了该问题。

```
# 没有引用b.js
Hash: db1cd0692725fce995a5
Version: webpack 4.29.6
Time: 385ms
Built at: 2019-04-01 22:33:08
                                       Asset       Size  Chunks             Chunk Names
        index.be3352d5eaa9d5600659.bundle.js  141 bytes       0  [emitted]  index
runtime~index.2d07a8ea1f8f0d134e38.bundle.js   1.42 KiB       1  [emitted]  runtime~index
vendors~index.f4ba2d84461a5156e5a5.bundle.js   69.4 KiB       2  [emitted]  vendors~index

# 引用了b.js
Hash: 8035921800017145ae77
Version: webpack 4.29.6
Time: 362ms
Built at: 2019-04-01 22:34:31
                                       Asset       Size  Chunks             Chunk Names
        index.31d9f48061b1ab038701.bundle.js  163 bytes       0  [emitted]  index
runtime~index.2d07a8ea1f8f0d134e38.bundle.js   1.42 KiB       1  [emitted]  runtime~index
vendors~index.f4ba2d84461a5156e5a5.bundle.js   69.4 KiB       2  [emitted]  vendors~index
```