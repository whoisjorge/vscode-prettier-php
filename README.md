<div align="center">
  <img alt="VSCode" height="100" hspace="40" vspace="10"
    src="https://upload.wikimedia.org/wikipedia/commons/9/9a/Visual_Studio_Code_1.35_icon.svg">
  <img alt="Prettier" height="120"
    src="https://raw.githubusercontent.com/prettier/prettier-logo/master/images/prettier-icon-light.png">
  <img alt="PHP" height="100" hspace="25" vspace="10"
    src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/PHP-logo.svg/500px-PHP-logo.svg.png">
</div>

<h1 align="center">VSCode + Prettier PHP Plugin</h1>

> Basic setup of VSCode and Prettier to enforce a consistent coding style for the PHP language.

## Requirements

- [Node](https://nodejs.org/) (_LTS recommended_)
- [VSCode](https://code.visualstudio.com/) (_with recommended extensions installed_)

## Usage

```sh
npm install # or yarn
```

## Example

### Input

<!-- prettier-ignore -->
```php
<?php
array_map(function($arg1,$arg2) use ( $var1, $var2 ) {
    return $arg1+$arg2/($var+$var2);
}, array("complex"=>"code","with"=>
    function() {return "inconsistent";}
,"formatting"=>"is", "hard" => "to", "maintain"=>true));
```

### Output

```php
<?php

array_map(
  function ($arg1, $arg2) use ($var1, $var2) {
    return $arg1 + $arg2 / ($var + $var2);
  },
  [
    'complex' => 'code',
    'with' => function () {
      return 'inconsistent';
    },
    'formatting' => 'is',
    'hard' => 'to',
    'maintain' => true,
  ],
);
```

## Configuration

### Prettier for PHP

It's recommended to set at least the `phpVersion` option.

| Name               | Default   | Description                                                                                                                                                                                                                                                                          |
| ------------------ | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `phpVersion`       | `"5.4"`   | Allows specifying the PHP version you're using. If you're using PHP 7.1 or later, setting this option will make use of modern language features in the printed output. If you're using PHP 5.3 or lower, you'll have to set this option or Prettier will generate incompatible code. |
| `trailingCommaPHP` | `true`    | If set to `true`, trailing commas will be added wherever possible. <br> If set to `false`, no trailing commas are printed.                                                                                                                                                           |
| `braceStyle`       | `"psr-2"` | If set to `"psr-2"`, prettier will move open brace for code blocks (classes, functions and methods) onto new line. <br> If set to `"1tbs"`, prettier will move open brace for code blocks (classes, functions and methods) onto same line.                                           |

A [complete list of available options](https://github.com/prettier/plugin-php#configuration) can be found in the **prettier/plugin-php** repository.

### Ignoring code

Use `.prettierignore` to ignore (i.e. not reformat) certain files and folders completely.

Use `// prettier-ignore` comments to ignore parts of files.

### Caveats

- Formatting of files that contain mixed PHP and HTML is still considered unstable, see [plugin-php issues](https://github.com/prettier/plugin-php/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+label%3Ainline).
  - Another solution could be [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client).

## License

This is free software; you can redistribute it and/or modify it under the terms of the [MIT license](LICENSE).
