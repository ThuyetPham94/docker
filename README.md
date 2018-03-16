<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## Chaỵ các service

Ta sẽ chạy các services trên bằng command sau :

docker-compose up

(Ta có thể chọn option -d (detach) để tiến trình ẩn vào background khi hoàn tất)

Lần đầu chạy, command sẽ cần khoảng vài phút để pull về các image cần thiết. Nhưng lần thứ 2 trở đi nếu các chỉ định images không thay đổi thì thời gian chạy sẽ nhanh hơn nhiều do không phải tải lại các image nữa.

Đến đây ta sẽ cần chuẩn bị 1 số thiết lập cho laravel để project có thể sẵn sàng chạy được.

## Learning Laravel

Laravel has the most extensive and thorough documentation and video tutorial library of any modern web application framework. The [Laravel documentation](https://laravel.com/docs) is thorough, complete, and makes it a breeze to get started learning the framework.

If you're not in the mood to read, [Laracasts](https://laracasts.com) contains over 900 video tutorials on a range of topics including Laravel, modern PHP, unit testing, JavaScript, and more. Boost the skill level of yourself and your entire team by digging into our comprehensive video library.

## Thiết lập cho laravel

File enviroment : .env

cp .env-example .env
Generate key và optimze command :

docker-compose exec app php artisan key:generate
docker-compose exec app php artisan cache:clear

(Nếu bị lỗi không tìm thấy file .env thì hãy thử chạy với sudo)

docker-compose exec <service-name> <câu lệnh> : với câu lệnh ở trên, ta thấy ý nghĩa sẽ là chạy <câu lệnh> bên trong container của service <service-name>

Option :
docker-compose exec app php artisan migrate --seed
Migrate database. Nếu chạy không lỗi với "migrate successful" ta có thể yên tâm rằng kết nối giữa app với database là ok.

(Note : nếu command trả về lỗi không tìm thấy file hoặc khi docker-compose exec app ls -la nhận thấy các folder không được mount đúng cách, cấu trúc folder trong container không giống với ở thư mục host, có thể các bạn cần lệnh sudo ở docker-compose run ở trên)

Đến đây app đã sẵn sàng được sử dụng! với đường dẫn : http://0.0.0.0:8080 
## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](http://laravel.com/docs/contributions).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell at taylor@laravel.com. All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
