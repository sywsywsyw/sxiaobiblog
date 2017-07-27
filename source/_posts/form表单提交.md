---
title: form表单
date: 2017-07-27 21:03:35
tags:
categories: form
---

------

 $("form").submit(function(){
      var self = $(this);
       $.post(self.attr("action"), self.serialize(), success, "json");
      return false;
      function success(data){
        if( data.zt == 'ok' ){
          var index = top.layer.msg('Êý¾ÝÌá½»ÖÐ£¬ÇëÉÔºò',{icon: 16,time:false,shade:0.8});
          setTimeout(function(){
            top.layer.close(index);
            top.layer.msg("±à¼­³É¹¦£¡");
            layer.closeAll("iframe");
                  //Ë¢ÐÂ¸¸Ò³Ãæ
                  parent.location.reload();
           },2000);
        }
       }
      });

form ±íµ¥ÉèÖÃÎª disabled="disabled"  ¾ÍÎÞ·¨Ê¹ÓÃ ±íµ¥Ìá½»  Èç¹ûÒªÉèÖÃÖ»¶ÁÇëÉèÖÃ readonly="readonly" ÕâÑù²Å¿ÉÒÔÌá½»



ReadonlyºÍDisabledÊÇÓÃÔÚ±íµ¥ÖÐµÄÁ½¸öÊôÐÔ£¬ËüÃÇ¶¼ÄÜ¹»×öµ½Ê¹ÓÃ»§²»ÄÜ¹»¸ü¸Ä±íµ¥ÓòÖÐµÄÄÚÈÝ¡£µ«ÊÇËüÃÇÖ®¼äÓÐ×ÅÎ¢Ð¡µÄ²î±ð£¬×Ü½áÈçÏÂ£º
ReadonlyÖ»Õë¶Ôinput(text / password)ºÍtextareaÓÐÐ§£¬¶ødisabled¶ÔÓÚËùÓÐµÄ±íµ¥ÔªËØ¶¼ÓÐÐ§£¬°üÀ¨select, radio, checkbox, buttonµÈ¡£
µ«ÊÇ±íµ¥ÔªËØÔÚÊ¹ÓÃÁËdisabledºó£¬µ±ÎÒÃÇ½«±íµ¥ÒÔPOST»òGETµÄ·½Ê½Ìá½»µÄ»°£¬Õâ¸öÔªËØµÄÖµ²»»á±»´«µÝ³öÈ¥£¬¶øreadonly»á½«¸ÃÖµ´«µÝ³öÈ¥£¨ÕâÖÖÇé¿ö³öÏÖÔÚÎÒÃÇ½«Ä³¸ö±íµ¥ÖÐµÄtextareaÔªËØÉèÖÃÎªdisabled»òreadonly£¬µ«ÊÇsubmit buttonÈ´ÊÇ¿ÉÒÔÊ¹ÓÃµÄ£©¡£