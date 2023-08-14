# Generate & Run Swagger on GO 1.16.15
Date : 14-08-2023

### Requirement
```
- go v1.16.15
- github.com/go-swagger v0.27.0
- github.com/go-openapi/runtime v0.19.21 
- github.com/go-openapi/jsonpointer v0.19.5 
- github.com/go-openapi/validate v0.19.13 
- github.com/go-openapi/swag v0.20.0 
- github.com/go-openapi/strfmt v0.20.2 
- github.com/go-openapi/spec v0.20.0 
- github.com/go-openapi/loads v0.19.5 
- github.com/go-openapi/jsonreference v0.19.4 
- github.com/go-openapi/errors v0.19.9 
- github.com/go-openapi/analysis v0.19.16

- github.com/PuerkitoBio/purell v1.1.1
- github.com/PuerkitoBio/urlesc

- github.com/redocly/redoc 2.0.0
 
```

### Reference
- https://goswagger.io/
- https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/make.bat
- https://stackoverflow.com/questions/56413951/setting-up-go-swagger-for-first-time
- https://www.youtube.com/watch?v=07XhTqE-j8k&t=475s
- https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/main.go


## 1) Set GOMOD OFF
go env -w GO111MODULE=off


## 2) Clone github repo
### clone repo from (github.com/go-openapi)
```
git clone --depth 1 --branch v0.19.21 https://github.com/go-openapi/runtime.git
git clone --depth 1 --branch v0.19.5 https://github.com/go-openapi/jsonpointer.git
git clone --depth 1 --branch v0.19.13 https://github.com/go-openapi/validate.git
git clone --depth 1 --branch v0.20.0 https://github.com/go-openapi/swag.git
git clone --depth 1 --branch v0.20.2 https://github.com/go-openapi/strfmt.git
git clone --depth 1 --branch v0.20.0 https://github.com/go-openapi/spec.git
git clone --depth 1 --branch v0.19.5 https://github.com/go-openapi/loads.git
git clone --depth 1 --branch v0.19.4 https://github.com/go-openapi/jsonreference.git
git clone --depth 1 --branch v0.19.9 https://github.com/go-openapi/errors.git
git clone --depth 1 --branch v0.19.16 https://github.com/go-openapi/analysis.git
```

### 3) Clone repo from (github.com/PuerkitoBio)
```
git clone --depth 1 --branch v1.1.1 https://github.com/PuerkitoBio/purell
git clone https://github.com/PuerkitoBio/urlesc.git
```

## 4) Go get redoc ("version": "2.0.0")
```
go get -u github.com/redocly/redoc
```

## 5) See example swagger remarks on codes
```
# classification
https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/handlers/docs.go

# route : post
https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/handlers/post.go

# route : get
https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/handlers/get.go

# route : put
https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/handlers/put.go

# route : delete
https://github.com/nicholasjackson/building-microservices-youtube/blob/episode_7/product-api/handlers/delete.go
```

## 6) Generate swagger.yml file
```
swagger generate spec -o ./v1/swagger.yaml --scan-models
```

## 7) Routing Swagger on Main or Controller class
```
// Http.Dir files must be fullpath, and set on config file 
handler.Handle("/v1/swagger.yaml", http.FileServer(http.Dir("C:\\Users\\Deni Setiawan\\Data\\nexsoft\\nexchief\\2023-08-04 Implementasi Swagger UI Nexchief2\\NEXCHIEF2_GO_PATH\\src\\nexsoft.co.id\\nexchief2")))

// UI : use ReDoc
//handler.Handle("/v1/docs", middleware.Redoc(middleware.RedocOpts{SpecURL: "/v1/swagger.yaml", BasePath: "/v1"}, nil)).Methods("GET")

// UI : use Swagger-UI
handler.Handle("/v1/docs", middleware.SwaggerUI(middleware.SwaggerUIOpts{SpecURL: "/v1/swagger.yaml", BasePath: "/v1"}, nil)).Methods("GET")
```

## 8) Swagger Doc Link
```
# swagger web
http://localhost:9078/v1/docs

# swagger yml
http://localhost:9078/v1/swagger.yml
```