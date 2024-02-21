# 棒グラフ + 折れ線グラフ

~~~gnuplot {cmd=true hide=true output="html"}
# SVG形式で出力を設定
set terminal svg

# グリッドを表示
set grid

# タイトルと軸ラベルの設定
set title "Sample of Combined Bar and Line Chart"
set xlabel "X Axis (Units)"
set ylabel "Y Axis (Bar Chart Values)"
set y2label "Y2 Axis (Line Chart Values)"

# X軸とY軸の範囲を設定
set xrange [0.5:10.5]     # X軸はデータの範囲に合わせて調整
set yrange [0:35]     # Y軸はデータの範囲に合わせて調整
set y2range [0:1]     # Y2軸はデータの範囲に合わせて調整
set ytics nomirror    # Y軸の目盛りを左側にのみ表示
set y2tics            # Y2軸の目盛りを有効に

# ヒストグラムのスタイル設定
set style data histogram
set style fill solid 1
set boxwidth 0.5

# 凡例を下に配置
set key below

# 使用するデータファイルのパスを指定
datafile = "data/combined.dat"

# 棒グラフと折れ線グラフを重ねてプロット

plot datafile using 1:2 with boxes       axis x1y1 title "Bar chart", \
     datafile using 1:3 with linespoints axis x1y2 title "Line chart"

# 出力ファイルを設定し、再プロット(論文とかに使う用)
set terminal postscript eps enhanced color
set output "output/combined_plot.eps"
replot
~~~
