# 素材ファイルのダウンロード

以下のサイトから、素材ファイルをダウンロードします。

> https://github.com/h2ospace/wpj02

## phpMyAdminをセットアップする

コマンドラインに、以下を入力してください。

```
phpmyadmin-ctl install
```

## ログイン情報

|  |  |
|-----------|-----------------|
| ID        | wpjlivelesson02 |
| Password  | wpjwpjwpj123    |

# メンテナンスモードにする

.maintenance
```
<?php
$upgrading = time();
```

# meta_queryを使おう

## 女性だけに絞り込む

```
$results = get_posts(array(
    'meta_query' => array(
        array(
            'key' => 'gender',
            'value' => '女',
        ),
    )
));

foreach ($results as $post): setup_postdata($post);
    the_meta();
endforeach; wp_reset_postdata();
```

## 女性の 30歳以上に絞り込む

```
$results = get_posts(array(
    'meta_query' => array(
        array(
            'key' => 'gender',
            'value' => '女',
        ),
        array(
            'key' => 'age',
            'value' => '30',
            'compare' => '>',
            'type' => 'numeric',
        )
    )
));

foreach ($results as $post): setup_postdata($post);
    the_meta();
endforeach; wp_reset_postdata();
```