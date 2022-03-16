---
layout: post
title: "Laravel Testing"
---


1. PhpStorm setup

- Run tests in PhpStorm. Highlight test folder / file you want to run and then use appropriate keybinding.
- Setup key binding in Preferences >> Run context configuration (ctrl + shift) and run action (ctrl + R). 
- Need to have a cli intepreter installed in Preferences > Languages & Frameworks > PHP.
- Need to have a test framework setup in Preferences > Test Frameworks, select local phpunit autoloader.

2. Adding multiple factory instances

```php
User::factory()
    ->count(3)
    ->sequence(
        ['name' => 'Jim'],
        ['name' => 'Bob'],
        ['name' => 'Frank'],
    )
    ->create();
```

3. Factory relations

has() // for has
for() // for belongs
 
4. Testing forms

May need to assertRedirect, not that this contains a status assertion under the hood so you will get +1 assertions when running the test. Also look into spatie/flash package.

