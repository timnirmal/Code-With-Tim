# Basics

## Images

&lt;img&gt; tag is used. 

`src` \(source\), `alt` \(altenative text\), `width` an `height` are attributes

## Text

* Paragraph `<p> </p>`
* Headings `<h1> </h1>` - headings are avialable from &lt;h1&gt; to &lt;h6&gt;
* Break `<br>`

### Headings

{% hint style="info" %}
Headings automatically add white space to before and after of the text
{% endhint %}

{% hint style="warning" %}
Search engines use the headings to index the structure and content of your web pages.

Users often skim a page by its headings. It is important to use headings to show the document structure.
{% endhint %}

Fore bigger headings use CSS,

```markup
<h1 style="font-size:60px;"> Heading 1 </h1>
```

### 

### Paragraph

{% hint style="success" %}
&lt;p&gt;   &lt;pre&gt;   &lt;hr&gt;   &lt;br&gt;
{% endhint %}

{% hint style="warning" %}
HTML don't consider white spaces and new lines.
{% endhint %}

So by using `<pre>` tag we can add whitespaces and new lines

{% tabs %}
{% tab title="<p>" %}
```markup
<p>
This is a Paragraph.
But in here no         whitespaces or

New lines are considered.
</p>
```
{% endtab %}

{% tab title="<pre>" %}
```markup
<pre>
This is pre tag.
In here           whitespaces and

New lines are possible.
</pre>
```
{% endtab %}
{% endtabs %}

`<hr>` - Line is created

`<br>` - Break the paragraph

##  Quotation and Citation Elements



{% page-ref page="quotation-and-citation-elements.md" %}



