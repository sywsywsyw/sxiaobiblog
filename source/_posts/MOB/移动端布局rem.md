---
title: 移动端布局rem
date: 2016-05-26 22:17:38
tags:
categories: MOB
---
------

<!-- more -->

```bash
@mixin userem($size){
	$shebei-list:320px,375px,360px,384px,414px,460px,640px;
	@each $shebei in $shebei-list{
		@media  screen and(min-width: $shebei){
			html{
				font-size:100px * ($shebei/$size);
			}
		}
	}
}
@include userem(640px)

.item{
	height: 0.88rem;
	background: red;
}
```

@media screen and (min-width: 320px) {
  html {
    font-size: 50px; } }

@media screen and (min-width: 375px) {
  html {
    font-size: 58.59375px; } }

@media screen and (min-width: 360px) {
  html {
    font-size: 56.25px; } }

@media screen and (min-width: 384px) {
  html {
    font-size: 60px; } }

@media screen and (min-width: 414px) {
  html {
    font-size: 64.6875px; } }

@media screen and (min-width: 460px) {
  html {
    font-size: 71.875px; } }

@media screen and (min-width: 640px) {
  html {
    font-size: 100px; } }

.item {
  height: 0.88rem;
  background: red; }
