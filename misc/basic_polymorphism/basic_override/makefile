# makefile
# プログラム名とオブジェクトファイル名.
PROGRAM = basic_override
OBJS	= main.o super.o sub.o

# コンパイラとオプション指定.
CXX = g++
CXXFLAGS = -g -Wall

# サフィックスルール適用対象の拡張子.
# 例えば、ターゲット名が“hoge.o”ならばmakeはこのサフィックスルールより“hoge.c”に依存していると判断して、コマンドを実行し“hoge.o”を生成する.
.SUFFIXES: .c .o

.PHONY:
all: ${PROGRAM}

# プライマリターゲット.
${PROGRAM}: ${OBJS}
	${CXX} -o $@ $^

# サフィックスルール.
.c .o:
	${CXX} ${CXXFLAGS} -c $<

# ヘッダファイルの依存関係.
# サフィックスルールを使ってもこれだけは自分で書かねばならない.
main.o: super.h sub.h
super.o: super.h
sub.o: super.h sub.h

# 中間ファイル削除用ターゲット.
.PHONY:
clean:
	${RM} ${PROGRAM} ${OBJS}
