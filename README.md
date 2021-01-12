# ProcessWire Dashboard Panel: Random Image

Display a random image in a dashboard panel.

Requires [ProcessWire Dashboard](https://github.com/daun/processwire-dashboard/).

## Usage

### Pick from list of URLs

```php
wire()->addHookAfter('Dashboard::getPanels', function ($event) {
    $panels = $event->return;

    $panels->add([
        'panel' => 'random-image',
        'size' => 'small',
        'data' => [
            'images' => [
                'https://via.placeholder.com/150/0000FF/808080',
                'https://via.placeholder.com/150/FF0000/FFFFFF',
                'https://via.placeholder.com/150/FFFF00/000000',
                'https://via.placeholder.com/150/000000/FFFFFF'
            ]
        ]
    ]);
});
```

### Pick from images in a folder

```php
wire()->addHookAfter('Dashboard::getPanels', function ($event) {
    $panels = $event->return;

    $panels->add([
        'panel' => 'random-image',
        'size' => 'small',
        'data' => [
            'dir' => 'dashboard/images', // relative to /site/templates/
        ]
    ]);
});
```

## Options

### images

Array of image URLs to pick from.

### dir

Directory name to look for images in.

### ratio

Aspect ratio to enforce for all images, e.g. `1.5`

### fit

How to fit images into the ratio container: `cover` or `contain`

### cache

Optionally cache the result of the random pick. À la Photo of the Day.

Takes any [value accepted by WireCache](https://processwire.com/api/ref/wire-cache/get/):
`3600`, `hourly`, `daily`, `tomorrow midnight`, etc.

## Contributing

Pull requests are welcome.

## License

[GPL-3.0](https://github.com/daun/processwire-dashboard/blob/master/LICENSE)
