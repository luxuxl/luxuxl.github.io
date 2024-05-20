> [可能只适合我自己的 RIME 配置 - 喵's StackHarbor](https://sh.alynx.one/posts/My-RIME/)
>
> [好用好看好玩的输入法 —— 鼠须管配置使用 | Lufs's Blog](https://blog.isteed.cc/post/squirrel-customization-2022/#全局设置)
>
> [Rime/小狼豪/鼠须管 输入法配置记 - 晨鹤部落格](https://chenhe.me/post/oh-my-rime/)
> 
> [rime中州韵小狼毫 保姆级安装配置教程 100种增强功能-CSDN博客](https://blog.csdn.net/weixin_42148809/article/details/135594098)
> 
> [小狼毫(Rime)配置打补丁原理\_小狼毫输入法设定没反应-CSDN博客](https://blog.csdn.net/weixin_42148809/article/details/124827354)
> 
> [RIME输入法方案配置手册 | 西山晴雪的知识笔记](https://xishansnow.github.io/posts/41ac964d)

## 简介

default.custom.yaml 用于设置输入法方案、切换输入法快捷键、中英文切换、翻页等等。

weasel.custom.yaml 用于设置托盘图标、指定软件默认英文输入、候选词横竖排列、界面布局、配色方案等等。

squirrel.yaml 

<方案标识>.custom.yaml 用于设置具体的输入方案。

## 配置路径

~/Library/Rime/

`/Library/Input Methods/Squirrel.app/Contents/SharedSupport/default.yaml`

## 外观

- 横向候选词
- 候选词个数 9
- 暗黑主题 lost_temple

## 强迫症、洁癖

删除其他 schema

## 中文标点替换

除了 `\` 用中文 `、`, 其他全用英文

此外, 逗号后面跟一个空格

## 默认英文

## 符号美化

->变成 → 
## vim 模式

## 配置

有的配置项写在 `schema` 中, 有的写在 `default` 中, 过于麻烦

现将所有的配置项写在 `schema` 文件中, 条理更加清晰

但为了保证能够生成配置文件, 需要在 `default.yaml` 文件中写入以下内容

```python
config_version: '0.40'

schema_list:
  - schema: self

# key_binder:
#   bindings:
    
recognizer:
  patterns:

# ascii_composer:
#   switch_key:
```

修改 `self.schema.yaml` 文件

```python
# Rime schema
# encoding: utf-8

############# basic ##############

schema:
  name: "自用简体输入法"
  schema_id: self
  version: 0.22

style:
  horizontal: true
  color_scheme: lost_temple

menu:
  page_size: 9

switches:
  - name: ascii_mode
    reset: 1
  - name: full_shape
    reset: 0
  - name: zh_simp
    reset: 1

############# engine ############
engine:
  filters:
    - simplifier
    - uniquifier
  processors:
    - ascii_composer     # 中英文切换
    - recognizer         # 没有 recognizer 会怎么样? 输入邮箱比如 aaa@ 会变成 啊啊啊@
    - key_binder         # 按键绑定
    - speller            # 接受并处理字符输入, 比如模糊音
    - punctuator         # 标点符号的行为
    - selector           # 数字选择, 当然也可以换成其他
    - navigator          # 输入时光标是否可以移动
    - express_editor
  segmentors:
    - ascii_segmentor
    - matcher
    - abc_segmentor
    - punct_segmentor
    - fallback_segmentor
  translators:
    - punct_translator
    - "table_translator@custom_phrase"
    - script_translator

############# filters ###############

simplifier:
  option_name: zh_simp

############# processors ################
ascii_composer:
  good_old_caps_lock: true
  switch_key:
    Caps_Lock: noop
    Control_L: noop
    Control_R: noop
    Shift_L: commit_code
    Shift_R: noop

recognizer:
  import_preset: default
  patterns:
    email: "^[A-Za-z][-_.0-9A-Za-z]*@.*$"
    uppercase: "[A-Z][-_+.'0-9A-Za-z]*$"
    url: "^(www[.]|https?:|ftp[.:]|mailto:|file:).*$|^[a-z]+[.].+$"

key_binder:
  bindings:
    # - {accept: space, send: Return, when: always}
    - {accept: Tab, send: Page_Down, when: has_menu}
    - {accept: "Shift+Tab", send: Page_Up, when: has_menu}

speller:
  auto_select: true
  delimiter: "'"
  algebra:
    - "erase/^xx$/"
    - "abbrev/^([a-z]).+$/$1/"
    - "abbrev/^([zcs]h).+$/$1/"
    - "derive/^([nl])ve$/$1ue/"
    - "derive/^([jqxy])u/$1v/"
    - "derive/([aeiou])ng$/$1gn/"
    - "derive/([dtngkhrzcs])o(u|ng)$/$1o/"
  alphabet: zyxwvutsrqponmlkjihgfedcba

punctuator:
  half_shape:
    ',' : ', '
    '.' : '.'
    '<' : '<'
    '>' : '>'
    '/' : '/'
    '?' : '?'
    ';' : ';'
    ':' : ': '
    "'" : "'"
    '"' : '"'
    '\' : '、'
    '|' : '|'
    '`' : '`'
    '~' : '~'
    '!' : '!'
    '@' : '@'
    '#' : '#'
    '%' : '%'
    '$' : '$'
    '^' : '^'
    '&' : '&'
    '*' : '*'
    '(' : '('
    ')' : ')'
    '-' : '-'
    '_' : '_'
    '+' : '+'
    '=' : '='
    '[' : '['
    ']' : ']'
    '{' : '{'
    '}' : '}'

################### segmentors ##############



################### translators ##############

translator:
  dictionary: luna_pinyin.extended
  preedit_format:
    - "xform/([nl])v/$1ü/"
    - "xform/([nl])ue/$1üe/"
    - "xform/([jqxy])v/$1u/"
  prism: luna_pinyin_simp
```

## 词库配置

修改 `luna_pinyin.extended.dict.yaml` 文件

```python
# Rime dictionary
# encoding: utf-8

---
name: luna_pinyin.extended
version: "2014.09.07"
sort: by_weight
use_preset_vocabulary: true
#下面的是本词库包含的所有词库，请根据需要开启/禁用，词条前添删#号即可开启/关闭词库。
#雙拼不支持 luna_pinyin.cn_en 詞庫，請用戶手動禁用。
import_tables:
  - luna_pinyin      #系统自带词库，无意外必须开启。
  # 以下两个通用扩展词库任选其一启用即可
  #- luna_pinyin.extended/luna_pinyin.practical      #A.挺全面的基本词库，含很丰富基本词条和组句语料，成语、俗语、诗词、人名词条不多。40w
  - luna_pinyin.extended/luna_pinyin.comprehensive   #B.很全面的一般性综合词库，除基本词条还包含文、史、餐、饮、医、药、生、化、金融、人名等等。80w
  # 分类扩展词库
  - luna_pinyin.extended/luna_pinyin.basis     #精选的基本词库，搜集于拼音加加、小麥、新酷音、維基百科等。
  - luna_pinyin.extended/luna_pinyin.hanyu  #汉语大词典，多为2字词。 2.2w
  - luna_pinyin.extended/luna_pinyin.net    #网络流行词，网上聊天常用的语句。3.6w
  - luna_pinyin.extended/luna_pinyin.diet   #饮食词汇大全，吃货必备。 15w
  - luna_pinyin.extended/luna_pinyin.chat   #日常聊天常用词，请叫我聊天达人。3.5k
  - luna_pinyin.extended/luna_pinyin.daily   #日常生活用词，衣、食、住、行、地放、称呼等等。31w
  - luna_pinyin.extended/luna_pinyin.website   #网站大全，百度、知乎神马的。5k
  - luna_pinyin.extended/luna_pinyin.computer_science  #电脑词汇，计算机科学相关，普通应用足够
  - luna_pinyin.extended/luna_pinyin.name    #人名词库，含中外名人。1w

  - luna_pinyin.extended/luna_pinyin.poetry #常用诗词，来源于唐宋诗词、千家詩、花間集、楚辭、詩經。 2.6w 
  - luna_pinyin.extended/luna_pinyin.idiom   #俗语，如题，含常用俗语，文青必备。6.6w
  - luna_pinyin.extended/luna_pinyin.classical  #成语，含常用成语、文青标配。2.8w

  #- luna_pinyin.extended/luna_pinyin.movie   #电影相关词汇，片名、演员、导演神马的。1.3w
  #- luna_pinyin.extended/luna_pinyin.music   #音乐相关词汇，歌曲、制作人、歌星之类的。2w
  #- luna_pinyin.extended/luna_pinyin.history   #历史词库，囊扩中国古代史、近代史、现代史和世界历史。10w
  #- luna_pinyin.extended/luna_pinyin.game  #游戏词库、单机/网游及相关词条。7k
  #- luna_pinyin.extended/luna_pinyin.moba   #Moba游戏用词，含LOL和DOTA及它的亲爹—魔兽的词条。5k
  #- luna_pinyin.extended/luna_pinyin.game_wow          # 魔兽世界词库
  #- luna_pinyin.extended/luna_pinyin.anime   #动漫词汇大全，动画、主要角色、声优等等。3w
  #- luna_pinyin.extended/luna_pinyin.city_beijing      # 北京地理信息词库，包含北京的常用地名
  #- luna_pinyin.extended/luna_pinyin.city_chongqing    # 重庆地理信息词库，包含重庆的常用地名
  #- luna_pinyin.extended/luna_pinyin.universities      # 国内高校名称词库
```
