<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8">
<!--

Nick Montfort
 Original Python program:
 8 January 2009, Taroko Gorge National Park, Taiwan and Eva Air Flight 28

Copyright (c) 2009 Nick Montfort <nickm@nickm.com>

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR
IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

-->
<style type="text/css">
/* <![CDATA[ */
body {
 background: #000088;
 color: #FFFFFF;
 margin: 0 24pt 0 24pt;
 font-family: Optima, sans-serif;
 font-size: 13pt;
}
div {
 height: 16pt;
}
a {
 color: #FFFFFF;
 text-decoration: none;
}
/* ]]> */
</style>
<script language="JavaScript" type="text/javascript">
var t=0;
var n=0;
var paths=0;
var above='bloke,mate,knacker'.split(',');
var below='ute,Commo,Lux,mudpig,job site,pooey,oval,bloke, shopping centre, servo pie, cold crowny,nail gun,jet ski, tinny'.split(',');
var trans='skid,fight,jobs up,work'.split(',');
var imper='Fight at,Inhabit,Get blind at,Talk about cars at,Enter, Get kicked out of, Piss up your pay at,Listen to Triple M at, Beleive the Herald Sun at';
imper=imper.split(',');
var intrans='drink,get blind,fuck eyed,shagged,hold,dream,yell, emote, supress'.split(',');
var s='s,'.split(',');
var texture='local'.split(',');
function rand_range(max) {
 return Math.floor(Math.random()*(max+1));
}
function choose(array) {
 return array[rand_range(array.length-1)];
}
function path() {
 var p=rand_range(1);
 var words=choose(above);
 if ((words=='forest')&&(rand_range(3)==1)) {
  words='monkeys '+choose(trans);
 } else {
  words+=s[p]+' '+choose(trans)+s[(p+1)%2];
 }
 words+=' the '+choose(below)+choose(s)+'.';
 return words;
}
function site() {
 var words='';
 if (rand_range(2)==1) {
  words+=choose(above);
 } else {
  words+=choose(below);
 }
 words+='s '+choose(intrans)+'.';
 return words;
}
function cave() {
 var adjs=(','+choose(texture)+' footy club').split(',');
 var target=1+rand_range(3);
 while (adjs.length>target) {
  adjs.splice(rand_range(adjs.length),1);
  }
 var words='\u00a0\u00a0'+choose(imper)+' the '+adjs.join(' ')+' \u2014';
 return words;
}
function do_line() {
 var main=document.getElementById('main');
 if (t<=25) {
  t+=1;
 } else {
  main.removeChild(document.getElementById('main').firstChild);
 }
 if (n===0) {
  text=' ';
 } else if (n==1) {
  paths=2+rand_range(2);
  text=path();
 } else if (n<paths) {
  text=site();
 } else if (n==paths) {
  text=path();
 } else if (n==paths+1) {
  text=' ';
 } else if (n==paths+2) {
  text=cave();
 } else {
  text=' ';
  n=0;
 }
 n+=1;
 text=text.substring(0,1).toUpperCase()+text.substring(1,text.length);
 last=document.createElement('div');
 last.appendChild(document.createTextNode(text));
 main.appendChild(last);
}
function poem() {
 setInterval(do_line, 1200);
} 
</script>
  <title>Smoko Gaz</title>
</head>
<body onload="poem()">
<div style="float:right; margin-top:12px; color:#FF0000; height:60pt">
<div>Smoko Gaz</div>
<div><a href="https://www.instagram.com/gerardstarlingphoto/">Gerard Starling</a></div>
</div>
<div id="main"></div>
</body>
</html>


