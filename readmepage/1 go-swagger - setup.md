# Setup Swagger on GO 1.16.15 
Date : 14-08-2023

## Requirement
```
- go v1.16.15
- go-swagger v0.27.0
```

### Reference
- https://goswagger.io/
- https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/make.bat
- https://stackoverflow.com/questions/56413951/setting-up-go-swagger-for-first-time
- https://www.youtube.com/watch?v=07XhTqE-j8k&t=475s
- https://github.com/go-swagger/go-swagger/releases/download/v0.27.0/swagger_windows_amd64.exe


## 1) Download swagger.exe v0.27.08-2023
- https://github.com/go-swagger/go-swagger/releases
- https://github.com/go-swagger/go-swagger/releases/download/v0.27.0/swagger_windows_amd64.exe 


## 2) Copy & Rename file swagger.exe
- rename file from `swagger_windows_amd64.exe` into `swagger.exe`
- copy file `swagger.exe` into bin folder on GLOBAL_GOPATH

```
C:\Users\Deni Setiawan\go
	\pkg\
	\src\
	\bin\
		swagger.exe
```


## 3) Create GO variable environtment
- GOPATH=C:\Users\Deni Setiawan\go
- GOROOT=%GOPATH%\go1.16.15
- GOBIN=%GOPATH%\bin

## 4) Add Go env into PATH variable
```
PATH=%GOPATH%
	 %GOROOT%\bin
	 %GOBIN%				
```


# 5) Swagger cek version
```
swagger version
```
```
version: v0.27.0
commit: 43c2774170504d87b104e3e4d68626aac2cd447d
```

# 6) Swagger generate doc (swagger.yml)
```
swagger generate spec -o ./v1/swagger.yaml --scan-models
```
```
./project/v1/
	swagger.yml
```
```
info: {}
paths: {}
swagger: "2.0"
```








