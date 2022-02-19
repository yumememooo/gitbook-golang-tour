---
description: >-
  MD5訊息摘要演算法（英語：MD5 Message-Digest
  Algorithm），一種被廣泛使用的密碼雜湊函數，可以產生出一個128位元（16位元組）的散列值（hash value），用於確保信息傳輸完整一致。
---

# md5加密庫(crypto/md5)

### MD5

MD5算法因其普遍、穩定、快速的特點，仍廣泛應用於普通數據的錯誤檢查領域。

1996年後被證實存在弱點，可以被加以破解，對於需要高度安全性的資料，專家一般建議改用其他演算法，如SHA-1。

Online generator md5 hash of a string:[http://www.md5.cz/](http://www.md5.cz)

範例程式

```
// Some code
package main

import (
	"crypto/md5"
	"encoding/hex"
	"fmt"

	"github.com/pkg/errors"
)

type User struct {
	Account string
	Pass    string
}

var m map[string]User

func main() {
	m = make(map[string]User)
	s := User{Account: "a", Pass: "b"}

	if err := registryUser(s); err != nil {
		fmt.Printf("registryUser failed %s", s.Account)
	}
	if err := registryUser(s); err != nil {
		fmt.Printf("registryUser failed %s", s.Account)
	}

	ls := User{Account: "a", Pass: "b"}
	err := loginUser(ls)
	if err != nil {
		fmt.Printf("User failed %s", ls.Account)
	}

	ls2 := User{Account: "aa", Pass: "bss"}

	if err := loginUser(ls2); err != nil {
		fmt.Printf("User failed %s", ls2.Account)
	}

}

func registryUser(s User) error {
	if _, ok := m[s.Account]; ok {
		return errors.Errorf("User alread Used.")
	}
	su := s
	su.Pass = hashBymd5(s.Pass)
	m[s.Account] = su
	return nil
}

func loginUser(u User) error {
	u, ok := m[u.Account]
	if !ok {
		return errors.Errorf("User not found.")
	}

	if u.Pass != hashBymd5(u.Pass) {
		return errors.Errorf("Pass not found.")
	}
	return nil
}

func hashBymd5(str string) string {
	h := md5.New()
	h.Write([]byte(str))
	return hex.EncodeToString(h.Sum(nil))
}

```
