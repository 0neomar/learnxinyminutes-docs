---
language: yaml
contributors:
  - ["Adam Brenecki", "https://github.com/adambrenecki"]
translators:
  - ["Zach Zhang", "https://github.com/checkcheckzz"]
filename: learnyaml-cn.yaml
lang: zh-cn
---

YAML��һ���������л����ԣ�����Ƴ�����ֱ�ӿ�д�ɶ��ġ�

����JSON���ϸ񳬼����������﷨�������з�������������Python������Python��һ����
YAML���������������Ʊ����


```yaml
# YAML�е�ע�⿴������������

################
# �������� #
################

# ���ǵĸ����� (�����������ļ�������) ������һ����ͼ��
# ���ȼ����ڱ���������һ���ֵ䣬����������
key: value
another_key: Another value goes here.
a_number_value: 100
scientific_notation: 1e+12
boolean: true
null_value: null
key with spaces: value
# ע�⵽�ַ�������Ҫ�����á����ǣ����ǿ��Ա����á�
"Keys can be quoted too.": "Useful if you want to put a ':' in your key."

# �����ַ����ȿ���д����һ��'���ֿ�'(ʹ�� |)��
# ����һ��'�۵���'(ʹ�� '>')��
literal_block: |
    This entire block of text will be the value of the 'literal_block' key,
    with line breaks being preserved.

    The literal continues until de-dented, and the leading indentation is
    stripped.

        Any lines that are 'more-indented' keep the rest of their indentation -
        these lines will be indented by 4 spaces.
folded_style: >
    This entire block of text will be the value of 'folded_style', but this
    time, all newlines will be replaced with a single space.

    Blank lines, like above, are converted to a newline character.

        'More-indented' lines keep their newlines, too -
        this text will appear over two lines.

####################
# �������� #
####################

# Ƕ����ͨ��������ɵġ�
a_nested_map:
    key: value
    another_key: Another Value
    another_nested_map:
        hello: hello

# ͼ�������ַ�����ֵ��
0.25: a float key

# ��ֵҲ�����Ƕ��ж�����?������ֵ�Ŀ�ʼ��
? |
    This is a key
    that has multiple lines
: and this is its value

# YAMLҲ�����ֵ�Ǽ������ͣ����Ǻܶ����Խ��ᱧԹ��

# ���� (�ȼ��ڱ������) ��������������
a_sequence:
    - Item 1
    - Item 2
    - 0.5 # sequences can contain disparate types
    - Item 4
    - key: value
      another_key: another_value
    -
        - This is a sequence
        - inside another sequence

# ��ΪYAML��JSON�ĳ�������Ҳ����дJSON���ĵ�ͼ�����У�
json_map: {"key": "value"}
json_seq: [3, 2, 1, "takeoff"]

#######################
# �����YAML�ص� #
#######################

# YAML����һ��������ص��'ê'��������򵥵��������ļ����ظ����ݡ�
# ������ֵ��������ͬ��ֵ��
anchored_content: &anchor_name This string will appear as the value of two keys.
other_anchor: *anchor_name

# YAML���б�ǩ�������������ʾ���������͡�
explicit_string: !!str 0.5
# һЩ������ʵ���ض����Եı�ǩ���������Ϊ��Python�ĸ������͡�
python_complex_number: !!python/complex 1+2j

####################
# �����YAML���� #
####################

# �ַ��������ֲ��ǽ��е�YAML�������ı�����
# ISO ��ʽ�����ں�����ʱ������Ҳ�ǿ��Ա������ġ�
datetime: 2001-12-15T02:59:43.1Z
datetime_with_spaces: 2001-12-14 21:59:43.10 -5
date: 2002-12-14

# ���!!binary��ǩ����һ���ַ���ʵ������һ��������blob��base64�����ʾ��
gif_file: !!binary |
    R0lGODlhDAAMAIQAAP//9/X17unp5WZmZgAAAOfn515eXvPz7Y6OjuDg4J+fn5
    OTk6enp56enmlpaWNjY6Ojo4SEhP/++f/++f/++f/++f/++f/++f/++f/++f/+
    +f/++f/++f/++f/++f/++SH+Dk1hZGUgd2l0aCBHSU1QACwAAAAADAAMAAAFLC
    AgjoEwnuNAFOhpEMTRiggcz4BNJHrv/zCFcLiwMWYNG84BwwEeECcgggoBADs=

# YAML����һ���������ͣ�����������������
set:
    ? item1
    ? item2
    ? item3

# ��Pythonһ�������Ͻ�����null��ֵ�ĵ�ͼ������ļ��ϵȼ��ڣ�
set2:
    item1: null
    item2: null
    item3: null
```
