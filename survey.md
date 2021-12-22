## npm package
## nookies
・CSRの場合はブラウザからcookieの情報を取得できるが、SSRの場合は取得できない。
```
クライアントでレンダリングしている場合
console.log(document.cookie); // accessToken=test1234;

SSRの場合
console.log(document.cookie); // ReferenceError: document is not defined
```
・nookiesを使うことでこの問題を回避することができる
```
import nookies from 'nookies';
export const getServerSideProps: GetServerSideProps = async (ctx) => {
  const cookies = nookies.get(ctx);
}
```
ctxを渡すことでcookieをObjectにして返してくれる
https://qiita.com/maedakei0817/items/1c5efc9d9f45c73dcbe0

## `<form>`のデフォルトの挙動
form要素に送信先が指定されていない場合、現在のURLに対してフォームの内容を送信してしまう。
現在のURLに対してフォームの送信が行われると、結果的にページがリロードされてしまいます。

https://qiita.com/yokoto/items/27c56ebc4b818167ef9e
