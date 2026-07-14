# Islander — Báo cáo Mô hình hoá thống kê (Bài thực hành 4)

Phân tích ANOVA nhiều nhân tố trên bộ dữ liệu [Memory Test on Drugged Islanders Data](https://www.kaggle.com/datasets/steveahn/memory-test-on-drugged-islanders-data) (Almohalwas, UCLA), nhằm xác định các nhân tố (loại thuốc, hàm lượng, loại ký ức gợi nhớ) ảnh hưởng đến khả năng gợi nhớ của người tham gia thử nghiệm.

## Cấu trúc thư mục

```
Islander-/
├── main.Rmd                # File tổng hợp — knit file này để ra báo cáo cuối cùng
├── header-includes.tex     # Gói LaTeX bổ sung cho main.Rmd (tikz, tắt trang tiêu đề mặc định)
├── Islander_data.csv        # Dữ liệu gốc
├── README.md
└── parts/                   # Các phần nội dung, được main.Rmd include làm child document
    ├── DatVanDe.Rmd          # Đặt vấn đề
    ├── PhanChinh_1_2.Rmd     # Yêu cầu 1-2: Tiền xử lý dữ liệu + Trực quan hoá
    ├── PhanChinh_3.Rmd       # Yêu cầu 3: ANOVA k nhân tố (k ≥ 2)
    ├── PhanChinh_4.Rmd       # Yêu cầu 4: Kiểm tra giả định mô hình, nhận xét, kết luận
    ├── PhanChinh_5.Rmd       # Yêu cầu 5: Đề xuất cải tiến / phân tích khác
    ├── Yeucauphu_1.Rmd       # Mở rộng: xây dựng mô hình Repeated Measures/Mixed ANOVA (Time)
    ├── Yeucauphu_2.Rmd       # Mở rộng: kiểm định hiệu ứng chính & tương tác với Time
    ├── Yeucauphu_3.Rmd       # Mở rộng: so sánh với mô hình ANOVA nhiều nhân tố
    └── Yeucauphu_4.Rmd       # Mở rộng: nhận xét ưu điểm, hạn chế giữa hai cách tiếp cận
```

## Yêu cầu môi trường

- R (khuyến nghị bản mới nhất) và [RStudio](https://posit.co/download/rstudio-desktop/) hoặc VS Code + R extension.
- Các gói R: `tidyverse`, `knitr`, `kableExtra`, `gridExtra`, `scales`, `here`, `showtext`, `sysfonts`.
- Bản phân phối LaTeX có `xelatex` để xuất PDF (khuyến nghị [TinyTeX](https://yihui.org/tinytex/): `tinytex::install_tinytex()`), do trang bìa dùng TikZ và font Times New Roman qua `showtext`.

Cài nhanh các gói R còn thiếu:

```r
install.packages(c("tidyverse", "knitr", "kableExtra", "gridExtra",
                    "scales", "here", "showtext", "sysfonts"))
```

## Cách build báo cáo

Chỉ knit **`main.Rmd`** (không knit riêng từng file trong `parts/`, vì các file con dùng `here::here()` để định vị `Islander_data.csv` ở thư mục gốc — chạy độc lập một file con vẫn hoạt động được nhờ `here`, nhưng trang bìa/mục lục/tài liệu tham khảo chỉ có khi knit qua `main.Rmd`):

```r
rmarkdown::render("main.Rmd")
```

hoặc bấm nút **Knit** trên `main.Rmd` trong RStudio/VS Code. Mặc định xuất cả PDF và HTML (khai báo trong YAML của `main.Rmd`).

Nếu muốn có logo trường trên trang bìa, đặt file `logo.png` vào thư mục gốc (`Islander-/`) — trang bìa sẽ tự nhận, không có file này thì vẫn build bình thường.

## Trạng thái nội dung

`DatVanDe.Rmd`, `PhanChinh_3/4/5.Rmd` và `Yeucauphu_1-4.Rmd` hiện còn trống, cần nhóm bổ sung nội dung tương ứng.

## Nhóm thực hiện — Nhóm 8

| Họ và Tên | Mã số HV |
|---|---|
| Trần Việt Hà | 25C23020 |
| Nguyễn Đình Mai Vi | 25C23005 |
| Vũ Hà Thư | 25C23004 |

Giảng viên hướng dẫn: TS. Nguyễn Thị Mộng Ngọc
