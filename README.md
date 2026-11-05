# zstd 1.5.5 on loongarch64

    cd zstd-1.5.5/build/cmake && mkdir build && cd build
    cmake -DBUILD_TESTING=OFF -DZSTD_BUILD_TESTS=OFF -DZSTD_BUILD_STATIC=ON \
          -DZSTD_BUILD_PROGRAMS=OFF -DZSTD_BUILD_SHARED=OFF \
          -DCMAKE_INSTALL_PREFIX=$PREFIX -DCMAKE_INSTALL_LIBDIR=lib ..
    cmake --build . -j4 && cmake --install .

零补丁。Arrow 的 `ARROW_WITH_ZSTD` 用它（Parquet zstd 压缩实测生效，压到 23%）。

## 更新（2026-11-04）

已随 `doris_be` 链接验证通过，0 错误。Arrow Parquet 的 zstd codec 实测把 20000 行压到 108KB（23%），未静默降级。
