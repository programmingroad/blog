先写个简单的demo，分析net/http的底层源码实现
```
// 请求处理函数
func indexHandler(w http.ResponseWriter, r *http.Request) {
	_, _ = io.WriteString(w, "hello, world!\n")
}

func main() {
	// 注册路由
	http.HandleFunc("/", indexHandler)
	// 创建服务并开启监听
	err := http.ListenAndServe(":8001", nil)
	if err != nil {
		log.Fatal("ListenAndServe: ", err)
	}
}
```

基于上述的demo，接下来我们一步一步分析。首先我们先进去 http.HandleFunc("/", indexHandler)

```
// HandleFunc registers the handler function for the given pattern
// in the DefaultServeMux.
// The documentation for ServeMux explains how patterns are matched.
func HandleFunc(pattern string, handler func(ResponseWriter, *Request)) {
	DefaultServeMux.HandleFunc(pattern, handler)
}
```
