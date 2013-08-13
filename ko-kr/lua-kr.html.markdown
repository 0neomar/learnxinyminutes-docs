---
language: lua
category: language
contributors:
    - ["Tyler Neylon", "http://tylerneylon.com/"]
translators:
    - ["wikibook", "http://wikibook.co.kr"]
lang: ko-kr
---

```lua
-- ��� �� ���� �� ��¥�� �ּ��� �ǹ��մϴ�.

--[[
     [�� ]�� �� ���� �߰��ϸ� ���� �� �ּ��� �˴ϴ�.
--]]

----------------------------------------------------
-- 1. ������ �帧 ����
----------------------------------------------------

num = 42  -- ��� ���ڴ� double�Դϴ�.
-- ��� �ʿ�� �����ϴ�. 64��Ʈ double�� 
-- ��Ȯ�� int ���� �����ϱ� ���� 52��Ʈ�� ������ 
-- �ֽ��ϴ�. 52��Ʈ ������ int ���� ���ؼ��� 
-- ��� ���е��� ���õ� ������ ������ �ʽ��ϴ�.

s = 'walternate'  -- ���̽�� ���� �Һ� ���ڿ�
t = "ū����ǥ�� �ᵵ �˴ϴ�"
u = [[ ���� ���ȣ��
       ���� �� ���ڿ���
       ��Ÿ���ϴ�.]]
t = nil  -- ������ t. ��ƴ� ������ �÷����� �����մϴ�.

-- ����� do/end�� ���� Ű����� ��Ÿ���ϴ�:
while num < 50 do
  num = num + 1  --  ++�� += ������ �����ڴ� �� �� �����ϴ�.
end

-- If ��:
if num > 40 then
  print('40 �̻�')
elseif s ~= 'walternate' then  -- ~=�� '���� �ʴ�'�Դϴ�.
  -- ���ϼ� �˻�� ���̽�� ���������� ==�Դϴ�. 
  -- ���ڿ����� �� �� �ֽ��ϴ�.
  io.write('not over 40\n')  -- �⺻������ stdout�� ���ϴ�.
else
  -- ������ �⺻������ ���� �����Դϴ�.
  thisIsGlobal = 5  -- ��Ÿ ǥ����� �Ϲ����Դϴ�.

  -- ������ ���� ������ ����� ����� ������ �����ϴ�:
  local line = io.read()  -- ���� stdin ���� �н��ϴ�

  -- ���ڿ� ���ῡ�� .. �����ڸ� ���ϴ�:
  print('�ܿ��� ���� �ֽ��ϴ�, ' .. line)
end

-- ������ ������ nil�� ��ȯ�մϴ�.
-- ���� �ڵ带 �����ص� ������ ���� �ʽ��ϴ�:
foo = anUnknownVariable  -- ���� foo�� nil�Դϴ�.

aBoolValue = false

-- nil�� false���� �������Դϴ�; 0�� ''�� ���Դϴ�!
if not aBoolValue then print('twas false') end

-- 'or'�� 'and'�� ���� ��(short-circuit)�˴ϴ�.
-- ���� �ڵ�� C/�ڹٽ�ũ��Ʈ�� a?b:c �����ڿ� ����մϴ�:
ans = aBoolValue and 'yes' or 'no'  --> 'no'

karlSum = 0
for i = 1, 100 do  -- �������� ������ ��ҵ� ���Ե˴ϴ�.
  karlSum = karlSum + i
end

-- ī��Ʈ �ٿ��� �� ���� "100, 1, -1"�� ������ ���ϴ�.
fredSum = 0
for j = 100, 1, -1 do fredSum = fredSum + j end

-- �Ϲ������� ������ begin, end[, step]�Դϴ�.

-- �� �ٸ� �ݺ��� ������ ������ �����ϴ�:
repeat
  print('�̷��� ���')
  num = num - 1
until num == 0


----------------------------------------------------
-- 2. �Լ�
----------------------------------------------------

function fib(n)
  if n < 2 then return n end
  return fib(n - 2) + fib(n - 1)
end

-- Ŭ������ �͸� �Լ��� ����� �� �ֽ��ϴ�:
function adder(x)
  -- ��ȯ�� �Լ��� adder�� ȣ��� �� �����ǰ� x��
  -- ���� �����˴ϴ�:
  return function (y) return x + y end
end
a1 = adder(9)
a2 = adder(36)
print(a1(16))  --> 25
print(a2(64))  --> 100

-- ��ȯ��, �Լ� ȣ��, �Ҵ繮�� ���̰� �ٸ�
-- ���� ����Ʈ�� ���ؼ��� ��� �����մϴ�.
-- ����Ʈ�� ���� �� ���� ���� nil�� �Ҵ�/��ȯ�ǰ�
-- ����Ʈ�� ���� �� ���� ���� ������ ���� �������ϴ�.

x, y, z = 1, 2, 3, 4
-- ���� x = 1, y = 2, z = 3�̰� 4�� �������ϴ�.

function bar(a, b, c)
  print(a, b, c)
  return 4, 8, 15, 16, 23, 42
end

x, y = bar('zaphod')  --> "zaphod  nil nil"�� ���
-- ���� x = 4, y = 8�̰� 15~42�� ���� �������ϴ�.

-- �Լ��� �ϱ� ��ü�̰�, ����/���� ��ȿ������ ����
-- �� �ֽ��ϴ�. �Ʒ��� �� �Լ��� �����ϴ�:
function f(x) return x * x end
f = function (x) return x * x end

-- �׸��� �Ʒ��� �� �Լ��� ���������Դϴ�:
local function g(x) return math.sin(x) end
local g; g  = function (x) return math.sin(x) end
-- 'local g'��� �����ϸ� g�� ���� �Լ��� ����ϴ�.

-- �׳����� �ﰢ �Լ��� ���� ������ �����մϴ�.

-- �Լ��� ȣ���� �� ���ڿ� �Ű������� �ϳ��� �����Ѵٸ�
-- ��ȣ�� ���� �ʾƵ� �˴ϴ�:
print 'hello'  -- �� �����մϴ�.


----------------------------------------------------
-- 3. ���̺�
----------------------------------------------------

-- ���̺� = ����� ������ ���� �ڷᱸ���μ�, ���� �迭�Դϴ�.
-- PHP�� �迭�̳� �ڹٽ�ũ��Ʈ�� ��ü�� ����ϸ�,
-- ����Ʈ�ε� ����� �� �ִ� �ؽ� ����� ��ųʸ��Դϴ�.

-- ���̺��� ��ųʸ�/������ ����ϱ�:

-- ��ųʸ� ���ͷ��� �⺻������ ���ڿ� Ű�� �����ϴ�:
t = {key1 = 'value1', key2 = false}

-- ���ڿ� Ű���� �ڹٽ�ũ��Ʈ�� ������ �� ǥ����� �� �� �ֽ��ϴ�:
print(t.key1)  -- 'value1'�� ���.
t.newKey = {}  -- �� Ű/�� ���� �߰�.
t.key2 = nil   -- ���̺��� key2�� ����.

-- (nil�� �ƴ�) ���� Ű�� ����ϴ� ���ͷ� ǥ���:
u = {['@!#'] = 'qbert', [{}] = 1729, [6.28] = 'tau'}
print(u[6.28])  -- "tau"�� ���

-- Ű ��Ī�� �⺻������ ���ڿ� ���ڿ��� ���ؼ��� ������ ������
-- ���̺� ���ؼ��� �ĺ��ڷ� �մϴ�.
a = u['@!#']  -- Now a = 'qbert'.
b = u[{}]     -- We might expect 1729, but it's nil:
a = u['@!#']  -- ���� a�� 'qbert'�Դϴ�.
b = u[{}]     -- 1729�� �����߰����� nil�Դϴ�:
-- Ž���� �����ϱ� ������ b�� nil�Դϴ�. Ž���� �����ϴ� ������
-- ���� Ű�� ���� ���� ������ �� ����� Ű�� ������ ��ü�� �ƴϱ�
-- �����Դϴ�. ���� ���ڿ� �� ���ڰ� �� �� �̽ļ� �ִ� Ű�Դϴ�.

-- ���̺� �ϳ��� �Ű������� ���ϴ� �Լ��� ȣ���� ���� ��ȣ�� �ʿ����� �ʽ��ϴ�:
function h(x) print(x.key1) end
h{key1 = 'Sonmi~451'}  -- 'Sonmi~451'�� ���.

for key, val in pairs(u) do  -- ���̺� ��ȸ
  print(key, val)
end

-- _G�� ��� ���� ����� ���� Ư���� ���̺��Դϴ�.
print(_G['_G'] == _G)  -- 'true'�� ���

-- ���̺��� ����Ʈ/�迭�� ����ϱ�:

-- ����Ʈ ���ͷ��� �Ϲ������� int Ű�� �����˴ϴ�:
v = {'value1', 'value2', 1.21, 'gigawatts'}
for i = 1, #v do  -- #v�� ����Ʈ v�� ũ���Դϴ�.
  print(v[i])  -- �ε����� 1���� �����մϴ�!! �������� �ƴմϴ�!
end
-- 'list'�� ���� Ÿ���� �ƴմϴ�. v�� ���ӵ� ������ Ű�� ���Ե�
-- ���̺��̰� ����Ʈ�� ��޵� ���Դϴ�.

----------------------------------------------------
-- 3.1 ��Ÿ���̺�� ��Ÿ�޼���
----------------------------------------------------

-- ���̺��� ���̺� ������ �����ε��� �����ϰ� �ϴ� ��Ÿ���̺���
-- ���� �� �ֽ��ϴ�. ���߿� ��Ÿ���̺��� ��� �ڹٽ�ũ��Ʈ 
-- ������Ÿ�԰� ���� ������ �����ϴ��� ���캸�ڽ��ϴ�.

f1 = {a = 1, b = 2}  -- �м� a/b�� ǥ��
f2 = {a = 2, b = 3}

-- ���� �ڵ�� �����մϴ�:
-- s = f1 + f2

metafraction = {}
function metafraction.__add(f1, f2)
  sum = {}
  sum.b = f1.b * f2.b
  sum.a = f1.a * f2.b + f2.a * f1.b
  return sum
end

setmetatable(f1, metafraction)
setmetatable(f2, metafraction)

s = f1 + f2  -- f1�� ��Ÿ���̺��� ������� __add(f1, f2)�� ȣ��

-- f1�� f2�� �ڹٽ�ũ��Ʈ�� ������Ÿ�԰� �޸� �� ��Ÿ���̺� ���� 
-- Ű�� ��� getmetatable(f1)�� ���� �޾ƿ;� �մϴ�.
-- ��Ÿ���̺��� __add ���� ��ư� �˰� �ִ� Ű�� ������ �Ϲ� ���̺��Դϴ�.

-- �׷����� ���� ���� s�� ��Ÿ���̺��� ������ ���� �ʱ� ������ �����մϴ�.
-- t = s + s
-- �Ʒ��� ���� Ŭ������ ������ ������ �̷��� ������ �߻����� �ʽ��ϴ�.

-- ��Ÿ���̺� ���� __index�� ���� �̿��� Ž���� �����ε��մϴ�:
defaultFavs = {animal = 'gru', food = 'donuts'}
myFavs = {food = 'pizza'}
setmetatable(myFavs, {__index = defaultFavs})
eatenBy = myFavs.animal  -- �����մϴ�! ������, ��Ÿ���̺�!

-- �������� ��Ÿ���̺� Ž���� ������ ��� ��Ÿ���̺��� __index ���� �̿���
-- ��õ��ϰ�, �̷� ������ �ݺ��˴ϴ�.

-- __index ���� �� �� ����ȭ�� Ž���� ���� function(tbl, key)��
-- �� ���� �ֽ��ϴ�.

-- __index, __add, ...�� ���� ��Ÿ�޼����� �մϴ�.
-- ������ ��Ÿ�޼��带 ���� ���̺��� ��ü ����Դϴ�.

-- __add(a, b)                     for a + b
-- __sub(a, b)                     for a - b
-- __mul(a, b)                     for a * b
-- __div(a, b)                     for a / b
-- __mod(a, b)                     for a % b
-- __pow(a, b)                     for a ^ b
-- __unm(a)                        for -a
-- __concat(a, b)                  for a .. b
-- __len(a)                        for #a
-- __eq(a, b)                      for a == b
-- __lt(a, b)                      for a < b
-- __le(a, b)                      for a <= b
-- __index(a, b)  <fn�̳� ���̺�>  for a.b
-- __newindex(a, b, c)             for a.b = c
-- __call(a, ...)                  for a(...)

----------------------------------------------------
-- 3.2 Ŭ���� ������ ���̺�� ���
----------------------------------------------------

-- ��ƿ��� Ŭ������ ����� ���� ������, ���̺�� ��Ÿ���̺���
-- �̿��� Ŭ������ ����� �پ��� ����� �ֽ��ϴ�.

-- ���� ������ ���� ������ �ϴ��� �����մϴ�.

Dog = {}                                   -- 1.

function Dog:new()                         -- 2.
  newObj = {sound = 'woof'}                -- 3.
  self.__index = self                      -- 4.
  return setmetatable(newObj, self)        -- 5.
end

function Dog:makeSound()                   -- 6.
  print('I say ' .. self.sound)
end

mrDog = Dog:new()                          -- 7.
mrDog:makeSound()  -- 'I say woof'         -- 8.

-- 1. Dog�� Ŭ����ó�� �����մϴ�. �����δ� ���̺��Դϴ�.
-- 2. function ���̺��:fn(...)��
--    function ���̺��.fn(self, ...)�� �����ϴ�.
--    :�� self��� ù ��° ���ڸ� �߰��� ���Դϴ�.
--    self�� ���� ��� ����� �ñ��ϴٸ� �Ʒ��� 7�� 8�� �о����.
-- 3. newObj�� Dog Ŭ������ �ν��Ͻ��� �˴ϴ�.
-- 4. self = �ν��Ͻ�ȭ�Ǵ� Ŭ����.
--    �ַ� self = Dog������ ����� �̿��ϸ� �̰��� �ٲ� �� �ֽ��ϴ�. 
--    newObj�� ��Ÿ���̺�� self�� __index�� ��� self�� �����ϸ�
--    newObj�� self�� �Լ��� ���� �˴ϴ�.
-- 5. ����: setmetatable�� ù ��° ���ڸ� ��ȯ�մϴ�.
-- 6. :�� 2���� ������ �Ͱ� ���� ���������� �̹����� self�� 
--    Ŭ������ �ƴ� �ν��Ͻ���� ������ �� �ֽ��ϴ�.
-- 7. Dog.new(Dog)�� �����Ƿ� new()������ self = Dog�Դϴ�.
-- 8. mrDog.makeSound(mrDog)�� �����Ƿ� self = mrDog�Դϴ�.

----------------------------------------------------

-- ��� ����:

LoudDog = Dog:new()                           -- 1.

function LoudDog:makeSound()
  s = self.sound .. ' '                       -- 2.
  print(s .. s .. s)
end

seymour = LoudDog:new()                       -- 3.
seymour:makeSound()  -- 'woof woof woof'      -- 4.

-- 1. LoudDog�� Dog�� �޼���� ������ ���� �˴ϴ�.
-- 2. self�� new()���� 'sound' Ű�� �����ϴ�. 3�� �����ϼ���.
-- 3. LoudDog.new(LoudDog)�� ����, LoudDog�� 'new' Ű�� ������
--    ��Ÿ���̺��� __index = Dog�̱� ������ Dog.new(LoudDog)����
--    ��ȯ�˴ϴ�.
--    ���: seymour�� ��Ÿ���̺��� LoudDog�̰� LoudDog.__index��
--    LoudDog�Դϴ�. ���� seymour.key�� seymour.key, 
--    LoudDog.key, Dog.key�� ���� ���̸�, ������ Ű�� � ���̺���
--    ���� ������� ���Դϴ�.
-- 4. 'makeSound' Ű�� LoudDog���� �߰��� �� �ֽ��ϴ�. 
--    �̰��� LoudDog.makeSound(seymour)�� �����ϴ�.

-- �ʿ��� ���, ���� Ŭ������ new()�� ��� Ŭ������ new()�� �����մϴ�.
function LoudDog:new()
  newObj = {}
  -- set up newObj
  self.__index = self
  return setmetatable(newObj, self)
end

----------------------------------------------------
-- 4. ���
----------------------------------------------------


--[[ ���⼭ �ּ��� �����ϸ� �� ��ũ��Ʈ�� ������ �κ��� 
--   ���� ������ ���°� �˴ϴ�.
```

```lua
-- mod.lua ������ ������ ������ ���ٰ� ������ ���ô�.
local M = {}

local function sayMyName()
  print('�̼ҷ�')
end

function M.sayHello()
  print('�ȳ��ϼ���')
  sayMyName()
end

return M

-- �� �ٸ� ���Ͽ����� mod.lua�� ����� �̿��� �� �ֽ��ϴ�.
local mod = require('mod')  -- mod.lua ������ ����

-- require�� ����� ���Խ�Ű�� ǥ��ȭ�� ����Դϴ�.
-- require�� ������ ���� �����մϴ�:     (ĳ�̵� ���� ���� ���. �ϴ� ����)
local mod = (function ()
  <mod.lua�� ����>
end)()
-- mod.lua�� �Լ��� ����ó�� �ǹǷ� mod.lua ���� ���� �����
-- �ۿ��� �� �� �����ϴ�.

-- ���� �ڵ尡 �����ϴ� ���� mod�� mod.lua�� M�� ���� �����Դϴ�.
mod.sayHello()  -- �̼ҷ� ������ �λ縦 �ǳܴϴ�.

-- ���� �ڵ带 �����ϸ� ������ �߻��մϴ�.
-- sayMyName�� mod.lua �ȿ����� �����ϱ� �����Դϴ�:
mod.sayMyName()  -- ����

-- require�� ��ȯ���� ĳ�̵ǹǷ� require�� ���� �� �����ص�
-- ������ �ִ� �� ���� ����˴ϴ�.

-- mod2.lua�� "print('Hi')"�� ��� �ִٰ� ������ ���ô�.
local a = require('mod2')  -- Hi!�� ���
local b = require('mod2')  -- print�� �������� ����. a=b

-- dofile�� require�� ��������� ĳ���� ���� �ʽ��ϴ�:
dofile('mod2')  --> Hi!
dofile('mod2')  --> Hi! (require�� �޸� �ٽ� �ѹ� �����)

-- loadfile�� ��� ������ �о�������� ���������� �ʽ��ϴ�
f = loadfile('mod2')  -- f()�� ȣ���ؾ� mod2.lua�� ����˴ϴ�.

-- loadstring�� ���ڿ��� ���� loadfile�Դϴ�.
g = loadstring('print(343)')  -- �Լ��� ��ȯ�մϴ�.
g()  -- 343�� ��µ˴ϴ�. ���������� �ƹ��͵� ��µ��� �ʽ��ϴ�.

--]]

```
## �����ڷ�

��Ƹ� ���� ���� ��������ߴ� ������ <a href="http://love2d.org/">Love 2D ���� ����</a>�� �̿��� 
������ ���� �� �־��� �����Դϴ�. �̰��� ���� ��Ƹ� ��� �����Դϴ�.

���� <a href="http://nova-fusion.com/2012/08/27/lua-for-programmers-part-1/">BlackBulletIV�� "���α׷��Ӹ� ���� ���"</a>��
�����߽��ϴ�. �״������� ���� <a href="http://www.lua.org/pil/contents.html">"���α׷��� ���"</a> å�� �о����ϴ�.
�׷��� ��Ƹ� ������ϴ�.

lua-users.org�� �ִ� <a href="http://lua-users.org/files/wiki_insecure/users/thomasl/luarefv51.pdf">ª�� ��� ���۷���</a>��
�о�θ� ��������� �𸣰ڽ��ϴ�.

���⼭�� ǥ�� ���̺귯���� ���ؼ��� �ٷ��� �ʾҽ��ϴ�.

* <a href="http://lua-users.org/wiki/StringLibraryTutorial">string ���̺귯��</a>
* <a href="http://lua-users.org/wiki/TableLibraryTutorial">table ���̺귯��</a>
* <a href="http://lua-users.org/wiki/MathLibraryTutorial">math ���̺귯��</a>
* <a href="http://lua-users.org/wiki/IoLibraryTutorial">io ���̺귯��</a>
* <a href="http://lua-users.org/wiki/OsLibraryTutorial">os ���̺귯��</a>

�׳����� �� ���� ��ü�� ��ȿ�� ��� ���α׷��Դϴ�. �� ������
learn.lua�� ������ �� "lua learn.lua"�� ������ ������!

�� ���� tylerneylon.com�� ó������ �ẻ ���̸�, 
<a href="https://gist.github.com/tylerneylon/5853042">Github�� Gist</a>������ Ȯ���� �� �ֽ��ϴ�.
��Ʒ� ��ſ� �ð��� ��������!