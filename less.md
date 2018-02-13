# Rikkeisoft Less Training [![GitHub release](http://rikkeisoft.com/wp-content/themes/rikkei/images/common/fbimg_new.png)](http://rikkeisoft.com/)
*Learn how to use lessc, build css with Gulp*

Một số vấn đề cơ bản của less, cách cài đặt và sử dụng. Sử dụng Gulp để buid từ less sang css.

## Install 

Cần cài đặt một vài môi trường sau:

Nodejs: 
```bash
    $ sudo apt-get install nodejs
```

Npm:
```bash
    $ sudo apt-get install npm
```

Cài đặt gulp-cli:
```bash
    $ npm install gulp-cli -g
```

Gulp và less:
```bash
    $ npm install gulp -g
    $ npm install -g less
    $ npm install gulp-less
```

## Sử dụng less

**Biến**

```bash
    @text-color: rgba(0,0,0,.69);

    .title{
        color: @text-color;
    }
```
Sau khi compile ta sẽ được đoạn mã CSS sau:

```bash
    .title {
        color: rgba(0,0,0,.69);
    }
```

**Import**

Nhập một file .less vào 1 file .less khác và sau đó có thể sử dụng toàn bộ các biến số trong file vừa nhập.

```bash
    @import "color"; //color.less -> Nếu là file less có thể bỏ qua hậu tố.
    @import "typo.css";
```

**Mixins - Kế thừa**

Xem ví dụ sau:

```bash
    .border {
        border: 1px solid #ddd;
        border-radius: 5px;
    }

    .content {
        width: 20vh;
        margin: 0 auto;
        .border;
    }
```

Sau khi compile bạn sẽ được mã CSS:

```bash
    .content {
        width: 20vh;
        margin: 0 auto;
        border: 1px solid #ddd;
        border-radius: 5px;
    }
```

**Các quy tắc lồng nhau**

Less cho phép bạn sử dụng quy tắc lồng nhau: 

*Với cách viết thông thường* 
```bash
    #header {
        color: black;
    }
    #header .navigation {
        font-size: 12px;
    }
    #header .logo {
        width: 300px;
    }
```

Trong Less, chúng ta có thể viết như sau:

```bash
    #header {
        color: black;
        .navigation {
            font-size: 12px;
        }
        .logo {
            width: 300px;
        }
    }
```

**Các phép toán trong less**

Các con số, màu sắc hoặc biến số đều có thể sử dụng để tính toán:

```bash
    @smallBannerHeight: 100px;

    .small-banner {
        height: @smallBannerHeight;    
    }
    .big-banner {
        height: @smallBannerHeight * 2;
    }
```

Và còn nhiều tính năng khác!

## Build less với Gulp

- Khởi tạo file `package.json` điền đẩy đủ các thuộc tính. Có thể sử dụng `npm init` để tự động khởi tạo.

- Tại thư mục root của project (nơi chứa file packages.json), dùng lệnh sau để cài đặt module Gulp vào project, đồng thời lưu thông tin vào file packages.json.

```bash
    $ npm install --save-dev gulp
```

- Cài đặt module gulp-less cho project:

```bash
    $ npm install --save-dev gulp-less
```

- Tạo file cấu hình gulp:

*Tại thư mục root của project, tạo file `gulpfile.js` với nội dung như sau:*

```bash
    var gulp = require('gulp');  
    var less = require('gulp-less');  
    var path = require('path');

    gulp.task('less', function () {  
    return gulp.src('less/**/*.less') //Với less là tên thư mục chứa các file less
        .pipe(less({
        paths: [ path.join(__dirname, 'less', 'includes') ]
        }))
        .pipe(gulp.dest('css')); //Thư mục đầu ra (nơi chứa các css sau khi compile)
    });

    gulp.task('default', ['less'], function() {

    });
```
*Cấu hình cho Gulp task tự động chạy. Task less sẽ tự động chạy mỗi lần phát hiện những thay đổi trên các file trong thư mục less:*


```bash
    var gulp = require('gulp');  
    var less = require('gulp-less');  
    var path = require('path');

    gulp.task('less', function () {  
    return gulp.src('./less/**/*.less')
        .pipe(less({
        paths: [ path.join(__dirname, 'less', 'includes') ]
        }))
        .pipe(gulp.dest('./css'));
    });

    gulp.task('watch', function() {  
    gulp.watch('./less/**/*.less', ['less']);
    });

    gulp.task('default', ['less', 'watch'], function() {

    });
```    

- Để chạy gulp sử dụng lệnh sau:

```bash
    $ gulp
```

hoặc

```bash
    $ gulp less
```

*Enjoy!!!! Thanks for reading ❤❤❤*





