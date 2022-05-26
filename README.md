# public_test
【gitとgithubのエラー(Windows)】

＞＞http接続
・URLが見つからない(URLは合っている)
→アカウント情報で競合がある可能性がある
　・資格情報マネージャーより、Windows資格情報を見る
　（自分以外の人のログイン情報を削除）
　→複数のログイン情報を保持したい場合
　　・urlにユーザーIDやパスワードを入れるやり方は廃止された
　　・二段階認証を用いている場合、おそらくssh接続しかやり方はない
　　（参考：https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/）

＞＞ssh接続
・~/.ssh内に公開鍵を作成をしてgithub側に追加しても接続できない
→sshファイル内にconfigファイルを作成する必要がある
　社内ネットワークの場合、色々と記入が必要
・CreateProcessW failed error:2
　posix_spawnp: No such file or directory
→conectにたどり着けていないことによるエラーの可能性
　Proxy commandを修正し、C:からconectまでのパスを記述する
・The authenticity of host '[ssh.github.com]:443 (<no hostip for proxy command>)' can't be established.
→これは未解決