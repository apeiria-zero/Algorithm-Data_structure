# LCM

Created: Apr 29, 2020 7:10 PM
Property: ape iria
Property 2: No
Tags: recursive

(a*b)/gcdで求まります。コードはgcdを参考にしてください。

↓オーバーフローに注意して解きましょう。

[C - Snack](https://atcoder.jp/contests/abc148/tasks/abc148_c)

Rubyで書いてみました

```ruby
def gcd(m,n)
  if n==0 then
    return m
  else
    return gcd(n,m%n)
  end
end

a,b=gets.split.map(&:to_i)
print a*b/gcd(a,b)
```