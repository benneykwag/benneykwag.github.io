---
layout: post
title:  "Getting Start Eui Framework"
date:   2016-04-08 01:25:50 +0900
categories: eui update
---
Eui 프레임웍은 ExtJS 6를 기반으로 하는 프레임웍입니다. 아직 프레임웍으로서의 완전한 형태를 제공하지 못하고 있지만
한국 실정에 맞는 컴포넌트와 라이브러리를 제공하려고 합니다.

Eui 프레임웍의 모든 파일은 깃허브에 공유하고 지속적으로 업데이트 합니다.

[https://github.com/benneykwag/eui][eui-site] 

Step 1 : 다운로드하기.
==
위의 링크를 클릭하면 깃허브 사이트로 이동합니다. 우측 "Download ZIP" 버튼을 클릭하면 Eui프레임웍과 샘플앱을
다운로드 할 수 있습니다.

Step 2 : 실행하기
==
압축 파일을 풀면 아래와 같은 파일 구조를 확인할 수 있습니다. 파일 디렉토리는 센차 워크스페이스이며 eui-sample폴더는
eui프레임웍을 이용한 샘플 앱입니다.

{% highlight ruby %}
- .sencha                   // 워크스페이스 설정 폴더.
- eui-sample                // 샘플용 앱
- ext                       // extjs 6용 sdk
- packages/local/eui-core   // eui프레임웍 코어.
            
{% endhighlight %}

eu-sample폴더로 이동해 sencha app watch를 실행하고 http://localhost:1841/eui-sample 브라우저를 통해 실행하면
샘플 앱이 기동됩니다.

Step 3 : 신규 앱에 eui-core 설정.
==

만약 새로 생성한 앱이 있다면 앱의 app.json 파일을 열고 아래와 같이 수정합니다.
{% highlight ruby %}
"requires": [
    // 
    "eui-core"
],

"css": [
    {
        // this entry uses an ant variable that is the calculated
        // value of the generated output css file for the app,
        // defined in .sencha/app/defaults.properties
        "path": "${build.out.css.path}",
        "bundle": true,
        "exclude": ["fashion"]
    },
    {   
        "path":"../packages/local/eui-core/resources/css/eui-theme.css"
    }
],
{% endhighlight %}

이제 app.js파일을 열고 아래처럼 eui프레임웍이 사용될 수 있도록 기본 코드를 삽입합니다.
{% highlight ruby %}

Ext.application({
    name: 'Eui.sample',

    extend: 'Eui.sample.Application',
    requires: [
        'Eui.sample.view.main.Main'
    ],
    init: function () {
        eui.Config.initLocaleMessage();
    },

    // The name of the initial view to create. With the classic toolkit this class
    // will gain a "viewport" plugin if it does not extend Ext.Viewport. With the
    // modern toolkit, the main view will be added to the Viewport.
    //
    mainView: 'Eui.sample.view.main.Main'
});


{% endhighlight %}

이후 sencha app watch나 refresh를 실행하면 사용할 준비는 완료됩니다.

[eui-site]: https://github.com/benneykwag/eui
