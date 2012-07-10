# SimpleApp

SimpleApp은 사람의 'Name'과 'Part'를 입력하면 테이블에 추가된 사람의 목록을 뿌려주는 간단한 웹어플리케이션이다.

이 데모는 BackboneJS와 RequireJS를 사용하여 웹어플리케이션을 만드는 방법을 가이드하기 위해 만들어졌다.

일반적인 웹사이트를 만드는것 처럼 jQuery를 이용하여 SimpleApp을 만들어보고, BackboneJS를 사용하여 구조화 시키고, RequireJS를 사용하여 모듈화 시켜나가는 과정을 볼수 있다.

## App
===
데모에 사용된 어플리케이션 목록이다.
app 폴더 밑에 각 프로젝트에 해당되는 폴더가 있다.

* [SimpleApp - jQuery](http://pillarlee16.github.com/SimpleApp/app/jquery/)
* [SimpleApp - BackboneJS](http://pillarlee16.github.com/SimpleApp/app/backbone/)
* [SimpleApp - BackboneJS and module](http://pillarlee16.github.com/SimpleApp/app/backbone-module/)
* [SimpleApp - BackboneJS and RequireJS](http://pillarlee16.github.com/SimpleApp/app/backbone-require/)


## Test
===
데모 어플리케이션중에 SimpleApp - BackboneJS and RequireJS를 단위 테스트를 해보았다. 테스트 프레임워크에는 Jasmine과 Sinon.js를 사용하였다. BackboneJS와 RequireJS를 사용한 웹어플리케이션에서 단위 테스트를 어떻게 하는지 보여주기 위한 데모로 테스트 코드 자체가 어플리케이션의 견고함을 보장하지는 않는다.

* [SimpleApp - Test](http://pillarlee16.github.com/SimpleApp/test/)


## Test Coverage
===
JSCoverage라는 라이브러리를 사용하여 Jasmine으로 수행한 단위 테스트의 커버리지를 측정해보았다. 커버리지를 측정하기 위해서는 사전에 JSCoverage를 사용하여 소스 코드를 복사해두어야 한다. 바로 실행해 볼 수 있도록 소스 코드를 <http://pillarlee16.github.com/SimpleApp/coverage/src-copy/> 경로에 미리 복사해두었다. 테스트 커버리지 검사를 실행시키는 방법은 다음과 같다.

1. <http://pillarlee16.github.com/SimpleApp/coverage/src-copy/jscoverage.html> 페이지를 브라우저로 연다.
2. URL 입력칸에 <http://pillarlee16.github.com/SimpleApp/test/coverage.html> 을 입력하고 Open in frame 버튼을 클릭한다.
3. Summary 탭에서 코드 커버리지를 확인한다.

## Build
===
SimpleApp - BackboneJS and RequireJS 를 Ant를 사용하여 테스트와 빌드를 자동화하였다. 빌드를 하기 위해 필요한 사전 준비물은 다음과 같이 4개가 필요하다.

* [Apache Ant](http://ant.apache.org/)
* [node.js](http://nodejs.org/)
* [PhantomJS](http://phantomjs.org/)
* [JSCoverage](http://siliconforks.com/jscoverage/)

위 4개의 프로그램을 설치하고 build.xml에 "jscoverage_home", "phantomjs_home", "node_home" property에 빌드하고자 하는 환경에 각 프로그램이 설치된 경로 변경해준다. 프로젝트의 asset 폴더안에 각 프로그램을 compile 해놓은 binary 파일들을 넣어놓기는 했지만, 정상적으로 작동하지 않을것으로 예상된다.

빌드 환경을 준비한 다음 프로젝트 루트 디렉토리에서 다음과 같은 명령어를 실행한다

	ant -f build.xml install
	
성공적으로 빌드가 수행되면 다음과 같은 로그를 볼 수 있다.

	Buildfile: /Users/pillarlee/git/SimpleApp/build.xml
		clean:
		coverage:
	    	[mkdir] Created dir: /Users/pillarlee/git/SimpleApp/build/src-copy
		     [exec] Instrumenting file view/DataRecordView.js
		     [exec] Instrumenting file view/DataListView.js
		     [exec] Instrumenting file view/DataInputView.js
		     [exec] Copying file template/dataRecordView.tmpl
		     [exec] Copying file template/dataListView.tmpl
		     [exec] Copying file template/dataInputView.tmpl
		     [exec] Instrumenting file model/Person.js
		     [exec] Copying file index.html
		     [exec] Instrumenting file collection/PersonList.js
		     [exec] Instrumenting file build.js
		     [exec] Instrumenting file app.backbone.js
		test:
		    [mkdir] Created dir: /Users/pillarlee/git/SimpleApp/build/test/report
		    [mkdir] Created dir: /Users/pillarlee/git/SimpleApp/build/test/report/cobertura
		    [mkdir] Created dir: /Users/pillarlee/git/SimpleApp/build/test/report/junit
		     [exec] Runner Started.
		     [exec] model.Person : 객체가 정상적으로 생성된다. ... 
		     [exec] Passed.
		     [exec] getName : attributes의 name의 값을 반환한다. ... 
		     [exec] Passed.
		     [exec] getName: 1 of 1 passed.
		     [exec] getPart : attributes의 part의 값을 반환한다. ... 
		     [exec] Passed.
		     [exec] getPart: 1 of 1 passed.
		     [exec] model.Person: 4 of 4 passed.
		     [exec] collection.PersonList : 객체가 정상적으로 생성된다. ... 
		     [exec] Passed.
		     [exec] collection.PersonList: 2 of 2 passed.
		     [exec] view.DataInputView : 객체가 정상적으로 생성된다. ... 
		     [exec] Passed.
		     [exec] view.DataInputView: 2 of 2 passed.
		     [exec] view.DataRecordView : 객체가 정상적으로 생성된다. ... 
		     [exec] Passed.
		     [exec] view.DataRecordView: 2 of 2 passed.
		     [exec] view.DataListView : 객체가 정상적으로 생성된다. ... 
		     [exec] Passed.
		     [exec] initialize : collection에 add 이벤트가 발생하면 addRecord가 호출된다. ... 
		     [exec] Passed.
		     [exec] initialize: 1 of 1 passed.
		     [exec] addRecord : tbody에 tr이 추가된다. ... 
		     [exec] Passed.
		     [exec] addRecord: 2 of 2 passed.
		     [exec] view.DataListView: 5 of 5 passed.
		     [exec] Runner Finished.
		     [exec] 9 specs, 0 failures in 0.026s.
		     [exec] 'waitFor()' finished in 331ms.
		build:
		     [exec] Tracing dependencies for: app.backbone
		     [exec] Uglifying file: /Users/pillarlee/git/SimpleApp/build/app/app.backbone.js
		     [exec] Uglifying file: /Users/pillarlee/git/SimpleApp/build/app/build.js
		     [exec] Uglifying file: /Users/pillarlee/git/SimpleApp/build/app/collection/PersonList.js
		     [exec] Uglifying file: /Users/pillarlee/git/SimpleApp/build/app/model/Person.js
		     [exec] Uglifying file: /Users/pillarlee/git/SimpleApp/build/app/view/DataInputView.js
		     [exec] Uglifying file: /Users/pillarlee/git/SimpleApp/build/app/view/DataListView.js
		     [exec] Uglifying file: /Users/pillarlee/git/SimpleApp/build/app/view/DataRecordView.js
		     [exec] app.backbone.js
		     [exec] ----------------
		     [exec] /Users/pillarlee/git/SimpleApp/asset/js/jquery-1.7.2.js
		     [exec] /Users/pillarlee/git/SimpleApp/asset/js/underscore.js
	 		 [exec] /Users/pillarlee/git/SimpleApp/asset/js/backbone.js
		     [exec] model/Person.js
		     [exec] collection/PersonList.js
		     [exec] /Users/pillarlee/git/SimpleApp/asset/js/text.js
		     [exec] text!template/dataInputView.tmpl
		     [exec] view/DataInputView.js
		     [exec] text!template/dataRecordView.tmpl
		     [exec] view/DataRecordView.js
		     [exec] text!template/dataListView.tmpl
		     [exec] view/DataListView.js
		     [exec] app.backbone.js
		dist:
		     [copy] Copying 1 file to /Users/pillarlee/git/SimpleApp/dist
		install:
		BUILD SUCCESSFUL
		Total time: 6 seconds
		
JSCoverage를 사용하여 소스 코드를 복사하고, PhantomJS를 사용하여 테스트 페이지를 실행하고, r.js를 사용하여 어플리케이션을 concatenation 한 다음 dist 폴더로 실제로 배포할 파일 (simpleapp.js)를 copy하는 과정을 로그를 통해 볼 수 있다.


## Slides
===
SimpleApp을 데모로 사용하여 자바스크립트 개발에 대한 세미나를 두 차례에 걸쳐 진행하였다. 세미나에 사용했던 발표자료를 링크해놓으니 필요할 경우 참조하면 도움이 될 것 같다.

* [대규모 자바스크립트 웹어플리케이션 개발하기](http://pillarlee16.github.com/SimpleApp/how-to-develope-a-large-scale-javascript-web-application.pdf)
* [자바스크립트 프로젝트의 단위 테스트, 테스트 커버리지 그리고 CI](http://pillarlee16.githbu.com/SimpleApp/javascript-project-unit-test-test-coverage-and-ci.pdf)