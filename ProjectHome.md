# Introduction #

This class allows to create HTML tags and render them efficiently.

# Why you should use it #
> It always generates valid HTML and XHTML code.
> It cans be used with lot of templates.
> It makes templates cleaner.
> It's easy to use and fast to execute.

# How to use it #
## Instanciate an HTML Writer ##
```
    require_once('HtmlTag.class.php');
    $html = HtmlTag::createElement();
```

It generates an empty container

> or

```
    require_once('HtmlTag.class.php');
    $html = HtmlTag::createElement('a');
```

It generates an 'a' tag

you can use any html tags : 'div','p','object',etc.

## Render tags ##
```
    echo(HtmlTag::createElement('a'));
```
## Simple tags ##
```
    echo $html->addElement('div')
    // <div></div>

    echo(HtmlTag::createElement('p')->setText('some content'));
    // <p>some content</p>
```

## Structured tags ##
```
    echo(HtmlTag::createElement('div')->addElement('a')->setText('a text'));
    // <div><a>a text</a></div>
```
```
    $container HtmlTag::createElement('div');
    $container->addElement('p')->setText('a text');
    $container->addElement('a')->setText('a link');
    echo( $container );
    // <div><p>a text</p><a>a link</a></div>
```
## Attributes ##

### Classics attributes (method : 'set') ###
```
    $tag = $html->addElement('a')
		->set('href','./sample.php')
		->set('id','myID')
		->setText('my link');
    echo( $tag );
    // <a href='./sample.php' id='myID'>my link</a>
```
### ID (method : 'id') ###
```
    $tag = $html->addElement('div')
		->id('myID');
    echo( $tag );
    // <div id='myID'>my link</a>
```
### Class management (method : 'addClass'/'removeClass') ###

```
    $tag = $html->addElement('div')
		->addClass('firstClass')
		->addClass('secondClass')
		->setText('my content')
		->removeClass('firstClass');
    echo( $tag );
    // <div class="secondClass">my content</div>
```

## More ##

> By default, contents are generate before text.
> For example :
```
    <div><a>sample</a>my text</div>
```

> You can reverse this order using 'showTextBeforeContent()' method
> Example :
```
    <div>my text<a>sample</a></div>
```