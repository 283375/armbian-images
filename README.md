# Armbian Images

白嫖 GitHub Actions 构建比较新的 Armbian 镜像。有 [orangepizero3](./userpatches/config-orangepizero3.conf) 和 [orangepi3b](./userpatches/config-orangepi3b.conf)。

纯自用，不做 bug 修复，大概不接 pr。~~搞得好像有什么可 pr 的一样~~

有问题请移步 Discussions。

## 神秘记录 1

```console
# (On WSL2 fedora-remix)
# for level in {1..9}; do
$ time xz -k -$level Armbian-unofficial_25.11.0-trunk_Orangepi3b_trixie_current_6.12.44.img
$ du -h $file && du $file && rm $file
```

| Level    | Compress Time | Diff   | File Size                          | Compression Ratio |
| -------- | ------------- | ------ | ---------------------------------- | ----------------- |
| Original | /             | /      | 2.4G<br><small>(2,457,600)</small> | /                 |
| 1        | 1m12.677s     | /      | 625M<br><small>(639,184)</small>   | 0.260             |
| 2        | 1m16.414s     | +4s    | 609M<br><small>(623,012)</small>   | 0.254             |
| 3        | 1m22.589s     | +6s    | 594M<br><small>(607,868)</small>   | 0.247             |
| 4        | 1m34.023s     | +11s   | 570M<br><small>(583,552)</small>   | 0.237             |
| 5        | 2m3.528s      | +29s   | 549M<br><small>(561,632)</small>   | 0.229             |
| 6        | 2m16.514s     | +13s   | 546M<br><small>(558,576)</small>   | 0.227             |
| 7        | 3m33.362s     | +1m17s | 537M<br><small>(549,396)</small>   | 0.224             |
| 8        | 7m0.957s      | +3m27s | 527M<br><small>(539,484)</small>   | 0.220             |
| 9        | 12m55.056s    | +5m54s | 506M<br><small>(517,488)</small>   | 0.211             |
