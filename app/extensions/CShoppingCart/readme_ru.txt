Установка и настройка
---------------------

1. В protected/config/main.php добавить:
~~~
[php]
'import' => array(
    //…
    'ext.CShoppingCart.*'
),
~~~

Использование
-------------
Модели, которым необходимо дать возможность добавления в корзину,
должны реализовать интерфейс ICartPosition:

~~~
[php]
class Book extends CActiveRecord implements ICartPosition {
    public static function model($className = __CLASS__) {
        return parent::model($className);
    }

    function getId(){
        return 'Book'.$this->id;
    }

    function getPrice(){
        return $this->price;
    }
}
~~~