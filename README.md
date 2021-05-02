# vue-type

## Project setup
```
npm install s
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

- vue 이슈
        props: {
            item: {
                type: String,
                required: true // 반드시 값을 내려 받는다.
            }
        },

v-model 은 한글입력시 한글자씩 반응이 늦는다는 vue2 한계점이 있다.
emit 과 props 를 이용하면 됨.
