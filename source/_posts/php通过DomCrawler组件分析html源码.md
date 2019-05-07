---
title: php通过DomCrawler组件分析html源码
date: 2019-04-15 13:17:42
categories: php
tags: [php, DomCrawler]
---
php的DomCrawler组件的使用，可以分析html和xml源码等。
# 安装DomCrawler

通过composer安装DomCrawler
`composer require symfony/dom-crawler`

安装之后就可以通过Xpath表达式方式操作，还有一种方式是通过类似Jquery的选择器操作html源码，但是需要安装CssSelector,本人对该方式比较熟悉所以以下例子便用这种方式。

# 安装CssSelector
通过composer安装CssSelector
`composer require symfony/css-selector`

<!-- more -->

# 基本使用
比如我们用DomCrawler爬取B站的视频排行榜，直接贴出php源代码。当然还有很多种使用方法，具体可查看[官方文档](https://symfony.com/doc/current/components/dom_crawler.html)或者[中文文档](http://symfonychina.com/doc/current/components/dom_crawler.html)

```php
require 'vendor/autoload.php';
use Symfony\Component\DomCrawler\Crawler;
$link = 'https://www.bilibili.com/ranking';
$html = file_get_contents($link);
$crawler = new Crawler($html);
//filter里面的就填写你需要获取的节点，类似jquery的方式填写
$result = $crawler->filter('.rank-list .rank-item .info .title')
     ->each(function($val, $i){
        return array(
          'title'=>$val->text(),
          'href'=>'https:' . $val->attr('href'),
        );
     });
var_export($result);
```
最后那里使用var_export打印出来的结果为
```
array (
  0 => 
  array (
    'title' => '这动画也太沙雕了吧！2019四月新番吐槽大盘点（第二弹）',
    'href' => 'https://www.bilibili.com/video/av49025020/',
  ),
  1 => 
  array (
    'title' => '【蔡徐坤】放荡不羁电音之舞',
    'href' => 'https://www.bilibili.com/video/av48828477/',
  ),
  2 => 
  array (
    'title' => '【城市拟人】《江山行歌》排骨教主/银临/winky诗/不才/三无MarBlue/KBShinya',
    'href' => 'https://www.bilibili.com/video/av49067889/',
  ),
  3 => 
  array (
    'title' => '手绘700帧！完美还原蔡徐坤打篮球！鸡你太美~',
    'href' => 'https://www.bilibili.com/video/av47441335/',
  ),
  4 => 
  array (
    'title' => 'BLACKPINK 美国Coachella音乐节 13首连唱 完整现场 超清',
    'href' => 'https://www.bilibili.com/video/av49156714/',
  ),
  5 => 
  array (
    'title' => '一部曾经感动过全B站的动画 —欺凌者不会得到救赎，但是',
    'href' => 'https://www.bilibili.com/video/av49004387/',
  ),
  6 => 
  array (
    'title' => '铲屎官买10斤上好牛肉，给猫咪做肉干，好吃得打起来！',
    'href' => 'https://www.bilibili.com/video/av49067407/',
  ),
  7 => 
  array (
    'title' => '字体侵权，我赔了10万元。他们算版权流氓吗？',
    'href' => 'https://www.bilibili.com/video/av49216130/',
  ),
  8 => 
  array (
    'title' => '【央视段子手】朱广权：我就是要用rap播新闻！',
    'href' => 'https://www.bilibili.com/video/av49067853/',
  ),
  9 => 
  array (
    'title' => '【C菌】世界唯一从不睡觉的人, 不仅活着竟然还能练瑜伽???【智障游戏合集第53期】',
    'href' => 'https://www.bilibili.com/video/av49211321/',
  ),
  10 => 
  array (
    'title' => '【大事件】苏大强虐心单曲首发，传新明星自走棋上线！ 暴走大事件第六季 15',
    'href' => 'https://www.bilibili.com/video/av49001132/',
  ),
  11 => 
  array (
    'title' => '【敖厂长】沙雕游戏主角死法超级华丽',
    'href' => 'https://www.bilibili.com/video/av48956942/',
  ),
  12 => 
  array (
    'title' => '油管转发150万视频：两小孩用口技还原小马丁的animals,在网易云找到了!',
    'href' => 'https://www.bilibili.com/video/av47739262/',
  ),
  13 => 
  array (
    'title' => '靠谱盘点35:Faker再次被坏女人伤害？场面一度失控！观众看完都哭了！！',
    'href' => 'https://www.bilibili.com/video/av49011661/',
  ),
  14 => 
  array (
    'title' => '救命！为什么整个b站都是蔡徐坤打篮球！',
    'href' => 'https://www.bilibili.com/video/av49097118/',
  ),
  15 => 
  array (
    'title' => '本以为我是中欧混血...结果...',
    'href' => 'https://www.bilibili.com/video/av49038614/',
  ),
  16 => 
  array (
    'title' => '【漫威/DC/踩点/1080p】前方高能！使人起鸡皮疙瘩的踩点与衔接的视觉盛宴！',
    'href' => 'https://www.bilibili.com/video/av46996647/',
  ),
  17 => 
  array (
    'title' => '阿衰(第一集)',
    'href' => 'https://www.bilibili.com/video/av48611776/',
  ),
  18 => 
  array (
    'title' => '告别塌鼻梁和大蒜鼻|徒手整鼻 拔高颜值|经验干货分享',
    'href' => 'https://www.bilibili.com/video/av49196400/',
  ),
  19 => 
  array (
    'title' => '海绵宝宝的beat上的Rap，炸了',
    'href' => 'https://www.bilibili.com/video/av48526858/',
  ),
  20 => 
  array (
    'title' => '【かや】小鹿亂撞♥【KAYA Ver.】',
    'href' => 'https://www.bilibili.com/video/av49030199/',
  ),
  21 => 
  array (
    'title' => '「字幕」女子66万买奔驰，还没出店就漏油，奔驰：按三包换发动机！',
    'href' => 'https://www.bilibili.com/video/av48981211/',
  ),
  22 => 
  array (
    'title' => '狂野牛仔老番茄',
    'href' => 'https://www.bilibili.com/video/av48922034/',
  ),
  23 => 
  array (
    'title' => '【超羞耻】萌妹竟被逼着翻唱hop！⁄(⁄ ⁄•⁄ω⁄•⁄ ⁄)⁄！',
    'href' => 'https://www.bilibili.com/video/av49016435/',
  ),
  24 => 
  array (
    'title' => '【老E】GBA上最猎奇的FPS射击游戏！',
    'href' => 'https://www.bilibili.com/video/av49130519/',
  ),
  25 => 
  array (
    'title' => '史上最蔡四月？这些四月番已经封神！快来一起吐槽他们吧【诚实吐槽】',
    'href' => 'https://www.bilibili.com/video/av49155579/',
  ),
  26 => 
  array (
    'title' => '手动一千帧抠图  当蔡徐坤加入银河护卫队',
    'href' => 'https://www.bilibili.com/video/av49023234/',
  ),
  27 => 
  array (
    'title' => '大司马和卢本伟 谁打篮球更像蔡徐坤？谁更美？',
    'href' => 'https://www.bilibili.com/video/av48713927/',
  ),
  28 => 
  array (
    'title' => '【燕小六】这破站就没有我小六吹不出来的曲子（歌曲串烧）',
    'href' => 'https://www.bilibili.com/video/av48860344/',
  ),
  29 => 
  array (
    'title' => '带好耳机，前方高能！无缝衔接 带你回顾那些经典场景【混剪/踩点/1080P】过瘾就够了！',
    'href' => 'https://www.bilibili.com/video/av48564837/',
  ),
  30 => 
  array (
    'title' => '【律师函警告】蔡徐坤鸡你太美的反击',
    'href' => 'https://www.bilibili.com/video/av49126533/',
  ),
  31 => 
  array (
    'title' => '求你了！别再这样练腹肌了！',
    'href' => 'https://www.bilibili.com/video/av48992580/',
  ),
  32 => 
  array (
    'title' => '【下载神器合集】分分钟各种满速下载！',
    'href' => 'https://www.bilibili.com/video/av48809112/',
  ),
  33 => 
  array (
    'title' => '【马云X马化腾】钱的魔力转圈圈',
    'href' => 'https://www.bilibili.com/video/av48888510/',
  ),
  34 => 
  array (
    'title' => '选手模仿蔡徐坤打篮球，评委:NBA像你这么打，明天就要解散了。',
    'href' => 'https://www.bilibili.com/video/av48996372/',
  ),
  35 => 
  array (
    'title' => '【散人】i wanna遭遇超精神污染打击 奇葩攻击不忍直视',
    'href' => 'https://www.bilibili.com/video/av49119545/',
  ),
  36 => 
  array (
    'title' => '某节目上有位男生模仿蔡徐坤打篮球，丁市长都忍不住了',
    'href' => 'https://www.bilibili.com/video/av48910590/',
  ),
  37 => 
  array (
    'title' => '【马云】你要的钱拿走',
    'href' => 'https://www.bilibili.com/video/av49080589/',
  ),
  38 => 
  array (
    'title' => '【黑执事】啵酱啵酱塞巴斯酱踩点燥起',
    'href' => 'https://www.bilibili.com/video/av48911748/',
  ),
  39 => 
  array (
    'title' => '【全明星】比利太美（鸡你太美）',
    'href' => 'https://www.bilibili.com/video/av49283739/',
  ),
  40 => 
  array (
    'title' => '【蔡徐坤X卢本伟】律师函警告',
    'href' => 'https://www.bilibili.com/video/av49159911/',
  ),
  41 => 
  array (
    'title' => '《创造营2019》主题曲《喊出我的名字》发起人迪丽热巴舞蹈版',
    'href' => 'https://www.bilibili.com/video/av49040544/',
  ),
  42 => 
  array (
    'title' => '【七代小丑/踩点/混剪/高燃】前方高能！欢乐与惊悚的踩点视觉盛宴！希斯莱杰诞辰40周年纪念。',
    'href' => 'https://www.bilibili.com/video/av48220814/',
  ),
  43 => 
  array (
    'title' => '【STN快报第三季16】快快快，冲冲冲，速通选手在行动',
    'href' => 'https://www.bilibili.com/video/av49089284/',
  ),
  44 => 
  array (
    'title' => '看一次笑一次！太魔性了',
    'href' => 'https://www.bilibili.com/video/av47801445/',
  ),
  45 => 
  array (
    'title' => '为什么日本妹子给人第一印象超好？日本人教我的自我提升术！up尝试后效果竟然这么好。。。',
    'href' => 'https://www.bilibili.com/video/av49184595/',
  ),
  46 => 
  array (
    'title' => '〔亿万级特效，史诗震撼级观看体验〕猫和老鼠鬼畜配音：打♂吔风波',
    'href' => 'https://www.bilibili.com/video/av48648661/',
  ),
  47 => 
  array (
    'title' => '粉丝竟然要求UP主模仿妖王来段HOP？【粉丝问答02】',
    'href' => 'https://www.bilibili.com/video/av49200653/',
  ),
  48 => 
  array (
    'title' => 'Love Story',
    'href' => 'https://www.bilibili.com/video/av49164364/',
  ),
  49 => 
  array (
    'title' => '对比蔡某同样是鬼畜，局座的回应。',
    'href' => 'https://www.bilibili.com/video/av49180702/',
  ),
  50 => 
  array (
    'title' => '徐老师来巡山211：妖姬女鬼式打法 摸一下就跑真刺激',
    'href' => 'https://www.bilibili.com/video/av49094991/',
  ),
  51 => 
  array (
    'title' => '小伙一次性怒吃五斤车厘子，只为体验车厘子吃到饱是什么感觉',
    'href' => 'https://www.bilibili.com/video/av49159781/',
  ),
  52 => 
  array (
    'title' => '查理九世背后的故事，你知道多少？',
    'href' => 'https://www.bilibili.com/video/av49004010/',
  ),
  53 => 
  array (
    'title' => '我一个中国人笑的浑身发抖…',
    'href' => 'https://www.bilibili.com/video/av47714764/',
  ),
  54 => 
  array (
    'title' => '化身修罗只为守护你！此刻世界将为之颤抖！',
    'href' => 'https://www.bilibili.com/video/av47014688/',
  ),
  55 => 
  array (
    'title' => '道德绑架，恶意孤立，无良记者！这部国产儿童美食动画电影竟暗讽现实《大耳朵图图之美食狂想曲》【国动手账本】',
    'href' => 'https://www.bilibili.com/video/av48986008/',
  ),
  56 => 
  array (
    'title' => '篮  球  人（高技术力）',
    'href' => 'https://www.bilibili.com/video/av48967832/',
  ),
  57 => 
  array (
    'title' => '因为一个视频，我被蔡徐坤粉丝骂到自闭！ 成了小姐姐最讨厌的人',
    'href' => 'https://www.bilibili.com/video/av48554006/',
  ),
  58 => 
  array (
    'title' => '华农兄弟：拿一点兄弟家的红薯喂母猪，顺便称一下小猪崽多重了',
    'href' => 'https://www.bilibili.com/video/av49046667/',
  ),
  59 => 
  array (
    'title' => '【哲学】绿♂色',
    'href' => 'https://www.bilibili.com/video/av48986114/',
  ),
  60 => 
  array (
    'title' => '千万不要跟声优斗表情包，否则你将毫无胜算Ⅻ',
    'href' => 'https://www.bilibili.com/video/av49068540/',
  ),
  61 => 
  array (
    'title' => 'すーぱーぬこになれんかった / まふまふ',
    'href' => 'https://www.bilibili.com/video/av49161878/',
  ),
  62 => 
  array (
    'title' => '【主播真会玩女神篇】70：菠萝留学囧途意外连连，刘飞儿亲密互动搞笑加倍',
    'href' => 'https://www.bilibili.com/video/av49097693/',
  ),
  63 => 
  array (
    'title' => '绝对防御逼迫敌人跳河！你从未见过的龟壳战车！丨《战争模拟器》正式版02',
    'href' => 'https://www.bilibili.com/video/av49038893/',
  ),
  64 => 
  array (
    'title' => '职业级不要笑挑战！等级：人类灭亡',
    'href' => 'https://www.bilibili.com/video/av48893578/',
  ),
  65 => 
  array (
    'title' => '实战印度街头小吃！吃一天真会拉肚子吗？',
    'href' => 'https://www.bilibili.com/video/av49075865/',
  ),
  66 => 
  array (
    'title' => '换个女团跳KILL THIS LOVE是什么感觉？',
    'href' => 'https://www.bilibili.com/video/av49106025/',
  ),
  67 => 
  array (
    'title' => '【吴亦凡VS蔡徐坤】鸡你太美',
    'href' => 'https://www.bilibili.com/video/av49154174/',
  ),
  68 => 
  array (
    'title' => '【游戏侦察冰】从河洛侠客风云传侵权被索赔2000万，看精神续作们的艰难之路',
    'href' => 'https://www.bilibili.com/video/av49046791/',
  ),
  69 => 
  array (
    'title' => '【楽小漫】PINK CAT ▶▷御姐喵喵驾到~ 【时隔三年的重制作】',
    'href' => 'https://www.bilibili.com/video/av49127290/',
  ),
  70 => 
  array (
    'title' => '【Aliga】内有恶犬 (`Д´)ﾉ Beast Dance！',
    'href' => 'https://www.bilibili.com/video/av49027661/',
  ),
  71 => 
  array (
    'title' => '我是学习忍术两年半的蔡徐坤',
    'href' => 'https://www.bilibili.com/video/av48848952/',
  ),
  72 => 
  array (
    'title' => '【励志短片】别懒惰久了，努力一下便以为是拼命?',
    'href' => 'https://www.bilibili.com/video/av46644313/',
  ),
  73 => 
  array (
    'title' => 'B站八部评分9.9的动漫神作',
    'href' => 'https://www.bilibili.com/video/av49014205/',
  ),
  74 => 
  array (
    'title' => '「卷发基础」|直板夹的正确打开方式|一只直板夹搞定所有的日常造型',
    'href' => 'https://www.bilibili.com/video/av48959498/',
  ),
  75 => 
  array (
    'title' => '移速挂？！脚本亚索？快到技能无法命中，一个视频看清所有外挂般的操作',
    'href' => 'https://www.bilibili.com/video/av49070361/',
  ),
  76 => 
  array (
    'title' => '【老丝长谈】你们对蔡徐坤们是不是太过分了',
    'href' => 'https://www.bilibili.com/video/av49019265/',
  ),
  77 => 
  array (
    'title' => '用抖音的方式打开动画片段会怎样？',
    'href' => 'https://www.bilibili.com/video/av48868904/',
  ),
  78 => 
  array (
    'title' => '当你加了一个菜徐鲲粉丝群…',
    'href' => 'https://www.bilibili.com/video/av47226898/',
  ),
  79 => 
  array (
    'title' => '我的“动漫”已死，祭奠逝去的旧时代',
    'href' => 'https://www.bilibili.com/video/av48605107/',
  ),
  80 => 
  array (
    'title' => '日本反鸡汤套路短片，人生没有奇迹！',
    'href' => 'https://www.bilibili.com/video/av47398032/',
  ),
  81 => 
  array (
    'title' => '适合一人偷偷看的后宫番，敌人变老婆？真是刺激到爆啊',
    'href' => 'https://www.bilibili.com/video/av49161436/',
  ),
  82 => 
  array (
    'title' => '【特效向】全明星の毁灭战争【下】：终局',
    'href' => 'https://www.bilibili.com/video/av49046465/',
  ),
  83 => 
  array (
    'title' => '瘦腿秘籍大公开/100%学生党可以操作/修长的双腿/安静无器械/拉长双腿线条/纤细修长/寝室运动/腿部塑形/肌肉腿拯救/水肿腿/运动健身/瘦身挑战/腿玩年',
    'href' => 'https://www.bilibili.com/video/av49082698/',
  ),
  84 => 
  array (
    'title' => '陪玩小姐姐竟然想让我"进洞"？【小潮国基网骗】',
    'href' => 'https://www.bilibili.com/video/av49178405/',
  ),
  85 => 
  array (
    'title' => '电影最TOP 123: 难以超越的奇幻史诗巨制《指环王》三部曲',
    'href' => 'https://www.bilibili.com/video/av48882824/',
  ),
  86 => 
  array (
    'title' => '2019最爽神片诞生！四月新番大吐槽第一弹！槽点巨骚！「泛式/新番妙妙屋15」',
    'href' => 'https://www.bilibili.com/video/av48973860/',
  ),
  87 => 
  array (
    'title' => '【狂三AWSL】人参赢家：只要胆量大，女王抢回家！',
    'href' => 'https://www.bilibili.com/video/av49206683/',
  ),
  88 => 
  array (
    'title' => '【逗鱼时刻】第197期 我们是怪盗军团',
    'href' => 'https://www.bilibili.com/video/av48992631/',
  ),
  89 => 
  array (
    'title' => '还记得当年一拳打穿屏幕的胖子吗',
    'href' => 'https://www.bilibili.com/video/av48968349/',
  ),
  90 => 
  array (
    'title' => '致命沙雕曲小心进来练出腹肌...《没有手机我要死了！》by 凯玟桑x尤超白',
    'href' => 'https://www.bilibili.com/video/av49194694/',
  ),
  91 => 
  array (
    'title' => '可以坐的保险杆',
    'href' => 'https://www.bilibili.com/video/av49035382/',
  ),
  92 => 
  array (
    'title' => '【160部动画混剪/无缝衔接流】三千世界 任我驰骋',
    'href' => 'https://www.bilibili.com/video/av46996628/',
  ),
  93 => 
  array (
    'title' => '这是款超级英雄的黑历史垃圾游戏',
    'href' => 'https://www.bilibili.com/video/av49176792/',
  ),
  94 => 
  array (
    'title' => '【三年特效】蔡徐坤除了打篮球，还会什么？',
    'href' => 'https://www.bilibili.com/video/av49273456/',
  ),
  95 => 
  array (
    'title' => '逍遥叹',
    'href' => 'https://www.bilibili.com/video/av47115841/',
  ),
  96 => 
  array (
    'title' => '黑洞本洞回应了',
    'href' => 'https://www.bilibili.com/video/av49076569/',
  ),
  97 => 
  array (
    'title' => '大密 | 吃播3年最硬核的一期 | 开箱',
    'href' => 'https://www.bilibili.com/video/av49059394/',
  ),
  98 => 
  array (
    'title' => '【小可儿×ilem】写给我家狗的歌（人声本家／专辑《2:3》收录曲）',
    'href' => 'https://www.bilibili.com/video/av48902566/',
  ),
  99 => 
  array (
    'title' => '88次炸薯条的血泪翻车史告诉你，这么做才能外酥里嫩！',
    'href' => 'https://www.bilibili.com/video/av48961432/',
  ),
)
```