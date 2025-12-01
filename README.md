<h1>TME歌詞相關api整理</h1>
歌詞都差不多的，畢竟是同一家。<br>
事實上，api遠不止這麼多，歡迎由___您___補充。
<h2>QQ音樂</h2>
<h3>搜索</h3>
<code>curl -X POST 'https://u.y.qq.com/cgi-bin/musicu.fcg' -H 'Content-Type: application/json' -d '{
        "req_0": {
            "method": "DoSearchForQQMusicDesktop",
            "module": "music.search.SearchCgiService",
            "param": {
                "query": "YOUR_SEARCH_KEYWORD",
                "num_per_page": NUMBER_OF_RESULTS
            }
        }
    }'
</code>
<h3>musicMid轉換</h3>
<code>curl -X GET 'https://c.y.qq.com/v8/fcg-bin/fcg_play_single_song.fcg?format=json&songmid=YOUR_SONG_MID'
</code>
沒有<code>format=json</code>也是可以正常請求的，mid會置於html標籤內。
<h3>獲取歌詞</h3>
<code>curl -X POST 'https://u.y.qq.com/cgi-bin/musicu.fcg' -H 'Content-Type: application/json' -d '{
    "music.musichallSong.PlayLyricInfo.GetPlayLyricInfo": {
      "module": "music.musichallSong.PlayLyricInfo",
      "method": "GetPlayLyricInfo",
      "param": {
        "trans": 1,
        "songID": YOUR_SONG_ID
      }
    }
  }'
</code>
<h2>酷我音樂</h2>
<h3>搜索</h3>
<code>curl -X GET 'https://kuwo.cn/search/searchMusicBykeyWord?ft=music&encoding=utf8&rn=NUMBER_OF_RESULTS&all=YOUR_SEARCH_KEYWORD&vipver=ANYTHING_HERE'
</code>
<code>curl -X GET 'http://search.kuwo.cn/r.s?vipver=ANYTHING_HERE&all=YOUR_SEARCH_KEYWORD&encoding=utf8&rformat=json&vermerge=1'
</code>
<h3>獲取歌詞</h3>
<code>curl -X GET 'https://kuwo.cn/openapi/v1/www/lyric/getlyric?musicId=YOUR_SONG_ID'
</code>
<h2>酷狗音樂</h2>
<h3>獲取歌曲hash</h3>
<code>curl -X GET 'http://mobileservice.kugou.com/api/v3/lyric/search?keyword=YOUR_SEARCH_KEYWORD'
</code>
或者使用https://www.cnblogs.com/wxd501/p/17071045.html 也是可以獲取hash的，數據結構更加清晰，但是需要cookies。
<h3>獲取歌詞列表</h3>
<code>curl -X GET 'http://krcs.kugou.com/search?hash=YOUR_HASH'
</code>
<h3>獲取歌詞</h3>
<code>curl -X GET 'http://lyrics.kugou.com/download?ver=ANYTHING_HERE&id=YOUR_ID&accesskey=YOUR_ACCESS_KEY'
</code>
<h3>轉換歌詞</h3>
https://github.com/veficos/krc2lrc/blob/master/python/krc2lrc.pyw
