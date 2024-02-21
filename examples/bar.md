# 棒グラフ

~~~gnuplot {cmd=true hide=true output="html"}
# SVG形式で出力を設定
set terminal svg

# グリッドを表示
set grid

# タイトルと軸ラベルの設定
set title "Sample Bar Chart"
set xlabel "Category"
set ylabel "Value"

# Y軸の範囲を設定(設定しない場合自動で決定される)
set yrange [0:30]

# ヒストグラムのスタイル設定
set style data histogram
set style fill solid 1
set boxwidth 1

# 凡例を下に配置
set key below

# 使用するデータファイルのパスを指定
datafile = "data/bar_data.dat"

# 棒グラフをプロット
plot datafile using 2:xtic(1) title "A"

# 出力ファイルを設定し、再プロット(論文とかに使う用)
set terminal postscript eps enhanced color
set output "output/bar_plot.eps"
replot
~~~

~~~gnuplot {cmd=true hide=true output="html"}
# SVG形式で出力を設定
set terminal svg

# グリッドを表示
set grid

# タイトルと軸ラベルの設定
set title "Sample Multiple Bar Chart"
set xlabel "Category"
set ylabel "Value"

# Y軸の範囲を設定(設定しない場合自動で決定される)
set yrange [0:30]

# ヒストグラムのスタイル設定
set style data histograms
set style histogram clustered gap 1
set style fill solid 1.0 border -1
set boxwidth 1.0

# 凡例を下に配置
set key below

# 使用するデータファイルのパスを指定
datafile = "data/bar_data.dat"

# 棒グラフ(ヒストグラム)をプロット
plot datafile using 2:xtic(1) title "A", \
     datafile using 3         title "B", \
     datafile using 4         title "C"

# 出力ファイルを設定し、再プロット(論文とかに使う用)
set terminal postscript eps enhanced color
set output "output/multiple_bar_plot.eps"
replot
~~~