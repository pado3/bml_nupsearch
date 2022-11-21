# bml_nupsearch

「なろうワード検索」を元にして、n段上のパスから検索できるようにしてみました。<br />
（なろうワード検索 - https://scotomallc.com/it/a-word-search/ ）<br />
例えば「小説家になろう」の話中の語で1段上の場合は、その作品の中から検索します。2段上なら「なろう」サイト全体からの検索になります。<br />
<p>
ちょうど今朝のラグビーフランス代表戦の記事を読んでいる時に、ある人の記事を探したくなって、site:のパスを下げていきながら思いついた次第。<br />
記事の例　https://rugby-rp.com/2022/11/21/japan/92354
<p>
n段上のパスを生成するのは、次のサイトを参考にしました：<br />
JavaScriptだけで動的な相対ルートパスを実装する方法｜web制作のラソナ沖縄事業所スタッフブログ - https://okinawa.razona.jp/1533<br />
<p>
スクリプトは次の通り(n=1)：<br />
javascript:<br />
var n=1;<br />
var s=document.getSelection().toString();<br />
var p=location.host + location.pathname.replace(new RegExp('(?:\\\/+[^\\\/]*){0,' + ((n || 0) + 1) + '}$'), '/');<br />
if(!!s){p=p+"+"+s;}<br />
location.href="https://www.google.com/search?q=site:%22+p;<br />
<p>
ブックマーク用のワンライナーはこちらです(n=1)：<br />
javascript:var n=1;var s=document.getSelection().toString();var p=location.host + location.pathname.replace(new RegExp('(?:\\\/+[^\\\/]*){0,' + ((n || 0) + 1) + '}$'), '/');if(!!s){p=p+"+"+s;}location.href="https://www.google.com/search?q=site:%22+p;<br />
<p>
改変、および改変したものの配布は自己責任でご自由にどうぞ。ご参考まで<br />
