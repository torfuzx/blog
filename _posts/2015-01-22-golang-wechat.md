---
layout: default
title: go语言下的微信开发
---
=============

#验证消息真实性
####加密/校验流程如下：
1. 将token、timestamp、nonce三个参数进行字典序排序
2. 将三个参数字符串拼接成一个字符串进行sha1加密
3. 开发者获得加密后的字符串可与signature对比，标识该请求来源于微信

```
// Verify whether the request is from wechat server.
// http://mp.weixin.qq.com/wiki/4/2ccadaef44fe1e4b0322355c2312bfa8.html
func (c *App) CheckWechatSignature() revel.Result {
	// 1. Sort params `token`, `timestamp` and `nonce` in lexical order
	arr := []string{c.WechatToken, c.WechatTimestamp, c.WechatNonce}
	sort.Strings(arr)

	// 2. Concatenate the sorted strings, and apply sha1
	s := strings.Join(arr, "")
	hasher := sha1.New()
	hasher.Write([]byte(s))
	hs := hex.EncodeToString(hasher.Sum(nil))

	// 3. Compare it with the signature provided in the request
	//    - if the the comparison yields equal, then it is from wechat
	//    - if the not, then it is not from wechat
	if hs != c.WechatSignature {
		revel.WARN.Println("Rejected request from non-wechat server.")
		return c.RenderError(fmt.Errorf("Don't accept request other than wechat server."))
	}
	revel.INFO.Println("Accepted request fron wechat server.")

	if c.Request.Method == "GET" {
		revel.INFO.Println("Echo back to wechat server: %s", c.WechatEchoStr)
		return c.RenderText(c.WechatEchoStr)
	}

	return nil
}
```
