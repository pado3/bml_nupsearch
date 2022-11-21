# bml_nupsearch

「なろうワード検索」を元にして、n段上のパスから検索できるようにしてみました。
例えば「なろう」で1段上の場合は、その作品の中から検索します。2段上なら「なろう」全体からの検索になります。

ちょうど今朝のラグビーフランス代表戦の記事を読んでいる時に、ある人の記事を探したくなって、
site:のパスを下げていきながら思いついた次第。
例　https://rugby-rp.com/2022/11/21/japan/92354

n段上のパスを生成するのは、次のサイトを参考にしました：
JavaScriptだけで動的な相対ルートパスを実装する方法｜web制作のラソナ沖縄事業所スタッフブログ - https://okinawa.razona.jp/1533

スクリプトは次の通り：
javascript:
var n=1;
var s=document.getSelection().toString();
var p=location.host + location.pathname.replace(new RegExp('(?:\\\/+[^\\\/]*){0,' + ((n || 0) + 1) + '}$'), '/');
if(!!s){p=p+"+"+s;}
location.href="https://www.google.com/search?q=site:%22+p;

ブックマーク用のワンライナーはこちらです：
javascript:var n=1;var s=document.getSelection().toString();var p=location.host + location.pathname.replace(new RegExp('(?:\\\/+[^\\\/]*){0,' + ((n || 0) + 1) + '}$'), '/');if(!!s){p=p+"+"+s;}location.href="https://www.google.com/search?q=site:%22+p;

ご参考まで
