# speedradar-data

測速雷達（SpeedRadar）App 用的照相資料，每天自動更新。

- 資料來源：政府資料開放平臺（警政署、高公局、本島各縣市警察局／交通局，約 47 個資料集），依[政府資料開放授權條款](https://data.gov.tw/license)使用
- 國道路線：© OpenStreetMap 貢獻者（ODbL）
- 不含離島（澎湖、金門、連江）

## 檔案

| 檔案 | 內容 |
|---|---|
| `v1/meta.json` | 版本（產生時間）、筆數、`cameras.tsv.gz` 的 SHA-256、各資料來源狀態 |
| `v1/cameras.tsv.gz` | 全部照相（緯度、經度、速限、地址、方向、自訂、種類、來源），已修正錯誤座標 |
| `v1/pending.tsv.gz` | 只有地址、還沒轉成座標的資料 |
| `v1/changes.json` | 與上一版比較：新增、移除、搬動的照相 |

網址：`https://raw.githubusercontent.com/beachdayme49/speedradar-data/main/v1/meta.json`
（備援：`https://cdn.jsdelivr.net/gh/beachdayme49/speedradar-data@main/v1/meta.json`）

## 更新方式

- GitHub Actions 每天台灣時間 05:30 執行 `scraper/speedradar-scraper.jar`
- 作者電腦開機時也會跑一次（台灣 IP，補抓擋國外連線的縣市網站）
- 某個來源抓不到或筆數暴跌：沿用上一版該來源的資料；總筆數異常：不發佈
- 爬蟲程式碼在私人 repo（beachdayme49/SpeedRadar 的 `scraper/` 模組），這裡只放編好的 jar
