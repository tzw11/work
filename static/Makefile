.PHONY: clean static all

all:split Esplit

static:split Esplit
	@echo ">  make index.html"
	@mv split.html index.html
	@echo ">  make Eindex.html"
	@mv Esplit.html Eindex.html

inline:inline.html
	@rm -rf indexx.html index.css index.js split.html

Einline:Einline.html
	@rm -rf Eindexx.html index.css Eindex.js Esplit.html

split:split.html
	@rm -rf indexx.html inline.html

Esplit:Esplit.html
	@rm -rf Eindexx.html Einline.html

inline.html:indexx.html index.css index.js
	@echo ">  make inline.html"
	@node lib/inline.js indexx.html index.css index.js > inline.html

Einline.html:Eindexx.html index.css Eindex.js
	@echo ">  make Einline.html"
	@node lib/inline.js Eindexx.html index.css Eindex.js > Einline.html

split.html:indexx.html index.css index.js
	@echo ">  make split.html"
	@node lib/split.js indexx.html index.css index.js > split.html

Esplit.html:Eindexx.html index.css Eindex.js
	@echo ">  make Esplit.html"
	@node lib/split.js Eindexx.html index.css Eindex.js > Esplit.html

indexx.html:index.html
	@java -jar lib/compressor.jar index.html > indexx.html

Eindexx.html:Eindex.html
	@java -jar lib/compressor.jar Eindex.html > Eindexx.html

index.css:$(wildcard css/*.css)
	@echo ">  make index.css"
	@cd css && ../lib/uglifycss/uglifycss --ugly-comments bootstrap.min.css codemirror.css popush.css > ../index.css

index.js:$(wildcard js/*.js)
	@echo ">  make index.js"
	@cd js && ../lib/uglify-js/bin/uglifyjs conf.js jquery.min.js jquery.cookie.js socket.io.min.js firebase.js newMultiConnection.js bootstrap.min.js codemirror.js loadmode.js localization/zh-cn.js ie.js filelist.js userlist.js expressionlist.js popush.js room.js > ../index.js 2>/dev/null

Eindex.js:$(wildcard js/*.js)
	@echo ">  make Eindex.js"
	@cd js && ../lib/uglify-js/bin/uglifyjs conf.js jquery.min.js jquery.cookie.js socket.io.min.js firebase.js newMultiConnection.js bootstrap.min.js codemirror.js loadmode.js localization/cn-zh.js ie.js filelist.js userlist.js expressionlist.js popush.js room.js > ../Eindex.js 2>/dev/null

clean:
	@rm -rf indexx.html index.css index.js inline.html split.html
	@rm -rf Eindexx.html Einline.html Esplit.html Eindex.js
