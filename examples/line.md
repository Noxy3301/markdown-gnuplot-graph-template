# 折れ線グラフ

~~~gnuplot {cmd=true hide=true output="html"}
# SVG形式で出力を設定
set terminal svg

# グリッドを表示
set grid

# タイトルと軸ラベルの設定
set title "Sample Line Chart"
set xlabel "Time (s)"
set ylabel "Amplitude"

# Y軸の範囲を設定(設定しない場合自動で決定される)
set xrange [1:10]
set yrange [0:40]

# 折れ線グラフのスタイル設定

# 凡例を下に配置
set key below

# 使用するデータファイルのパスを指定
datafile = "data/line_data.dat"

# 折れ線グラフをプロット
plot datafile using 1:2 with linespoints title "A",\
     datafile using 1:3 with linespoints title "B"

# 出力ファイルを設定し、再プロット(論文とかに使う用)
set terminal postscript eps enhanced color
set output "output/line_plot.eps"
replot
~~~