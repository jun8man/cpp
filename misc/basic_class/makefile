# Makefile
#
# 基本的な書き方
# target name: dependent file1, dependent file2, dependent file3
#	command1
#	command2
#	command3
# -> dependent fileのうちどれか1つでも更新されるとコマンドが実行される
# マクロを使って汎用性を持たせることもできるが、それは別の機会に★

# これでもいいけど、更新されていないファイルまでコンパイルし直される.
# basic_class: main.cpp basic_class.cpp
# 	g++ -o basic_class main.cpp basic_class.cpp

# こうするとall以下に書かれた実行ファイルが全てmakeされる.
.PHONY: all
all: basic_class

# こうすると更新されたファイルだけコンパイルされる.
# -o オブジェクトファイルをリンクしてその結果をbasic_classとする.
basic_class: main.o basic_class.o
	g++ -o basic_class main.o basic_class.o

# -c でld(1)によるリンクを行わずに、ソースファイルごとに.oファイル(オブジェクトファイル)を作成する.
# ヘッダファイルの依存関係も記載しておかないとヘッダファイルの更新時にコンパイルされない.
main.o: main.cpp basic_class.h
	g++ -c main.cpp

basic_class.o: basic_class.cpp basic_class.h
	g++ -c basic_class.cpp

# make cleanで不要なファイル(中間生成物とか実行ファイルとか)を消す.
# ターゲット名(ここではclean)と同じ名前のファイルがあると変なことになるので.PHONYを使って避ける.
.PHONY: clean
clean:
	rm -f basic_class main.o basic_class.o