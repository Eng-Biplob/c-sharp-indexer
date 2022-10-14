<h1><span style="font-size: 14px;">Video Tutorial link:</span><a href="https://www.youtube.com/watch?v=km1hd9-dVz4&ab_channel=kudvenkat"><span style="font-size: 14px;">(3458) Part 65 - C# Tutorial - Indexers in c# - YouTube</span></a></h1>
<h1>C# Indexers</h1>
<p>An indexer is a special type of property that allows a class or a structure to be accessed like an array for its internal collection. C# allows us to define custom indexers, generic indexers, and also overload indexers.</p>
<p>An indexer can be defined the same way as property with <code>this</code> keyword and square brackets <code>[]</code>.</p>
<div>
    <div>Syntax</div>
    <div>
        <pre>&lt;return type&gt; this[&lt;parameter type&gt; index]
{
    get{
        // return the value from the specified index of an internal collection
    }
    set{
        // set values at the specified index in an internal collection
    }
}</pre>
    </div>
</div>
<p>The following example defines an indexer in the class.</p>
<div>
    <div>Example: Indexer</div>
    <div>
        <pre><code>class StringDataStore
{
    private string[] strArr = new string[10]; // internal data storage

    public string this[int index]
    {
        get
        {
            if (index &lt; 0 || index &gt;= strArr.Length)
                throw new IndexOutOfRangeException(&quot;Index out of range&quot;);

                return strArr[index];
        }

        set
        {
            if (index &lt; 0 ||  index &gt;= strArr.Length)
                throw new IndexOutOfRangeException(&quot;Index out of range&quot;);

            strArr[index] = value;
        }
    }
}</code></pre>
    </div>
    <div><br></div>
</div>
<p>The above <code>StringDataStore</code> class defines an indexer for its private array <code>strArr</code>. So now, you can use the <code>StringDataStore</code> like an array to add and retrieve string values from <code>strArr</code>, as shown below.</p>
<div>
    <div>Example: Indexer</div>
    <div>
        <pre><code>StringDataStore strStore = new StringDataStore();

strStore[0] = &quot;One&quot;;
strStore[1] = &quot;Two&quot;;
strStore[2] = &quot;Three&quot;;
strStore[3] = &quot;Four&quot;;
        
for(int i = 0; i &lt; 10 ; i++)
    Console.WriteLine(strStore[i]);
</code></pre>
    </div>
    <div><a href="https://www.tutorialsteacher.com/codeeditor?cid=cs-gLV3gD" target="_blank" title="Try this example code yourself">Try it</a></div>
</div>
<div>Output:</div>
<p><samp>One<br>Two<br>Three<br>Four</samp></p>
<p>You can use expression-bodied syntax for get and set from C# 7 onwards.</p>
<div>
    <div>Example: Indexer</div>
    <div>
        <pre><code>class StringDataStore
{
    private string[] strArr = new string[10]; // internal data storage

    public string this[int index]
    {
        get =&gt; strArr[index];

        set =&gt; strArr[index] = value;
    }
}</code></pre>
    </div>
    <div><a href="https://www.tutorialsteacher.com/codeeditor?cid=cs-lFGrgz" target="_blank" title="Try this example code yourself">Try it</a></div>
</div>
<div><br></div>
<h2>Generic Indexer</h2>
<p>Indexer can also be generic. The following <a href="https://www.tutorialsteacher.com/csharp/csharp-generics" target="_blank">generic</a> class includes generic indexer.</p>
<div>
    <div>Example: Generic Indexer</div>
    <div>
        <pre><code>class DataStore&lt;T&gt;
{
    private T[] store; 

    public DataStore()
    {
        store = new T[10];
    }

    public DataStore(int length)
    {
        store = new T[length];
    }

    public T this[int index]
    {
        get
        {
            if (index &lt; 0 &amp;&amp;  index &gt;= store.Length)
                throw new IndexOutOfRangeException(&quot;Index out of range&quot;);

                return store[index];
        }

        set
        {
            if (index &lt; 0 ||  index &gt;= store.Length)
                throw new IndexOutOfRangeException(&quot;Index out of range&quot;);

            store[index] = value;
        }
    }

    public int Length
    {
        get
        {
            return store.Length;
        }
    }
}
</code></pre>
    </div>
    <div><a href="https://www.tutorialsteacher.com/codeeditor?cid=cs-sKWvHa" target="_blank" title="Try this example code yourself">Try it</a></div>
</div>
<p>The above generic indexer can be used with any data type. The following example demonstrates the use of generic indexer.</p>
<div>
    <div>Example:</div>
    <div>
        <pre><code>DataStore&lt;int&gt; grades = new DataStore&lt;int&gt;();
grades[0] = 100;
grades[1] = 25;
grades[2] = 34;
grades[3] = 42;
grades[4] = 12;
grades[5] = 18;
grades[6] = 2;
grades[7] = 95;
grades[8] = 75;
grades[9] = 53;

for (int i = 0; i &lt; grades.Length;i++)
    Console.WriteLine(grades[i]);

DataStore&lt;string&gt; names = new DataStore&lt;string&gt;(5);
names[0] = &quot;Steve&quot;;
names[1] = &quot;Bill&quot;;
names[2] = &quot;James&quot;;
names[3] = &quot;Ram&quot;;
names[4] = &quot;Andy&quot;;

for (int i = 0; i &lt; names.Length;i++)
    Console.WriteLine(names[i]);
</code></pre>
    </div>
    <div><a href="https://www.tutorialsteacher.com/codeeditor?cid=cs-sKWvHa" target="_blank" title="Try this example code yourself">Try it</a></div>
</div>
<h2>Overload Indexer</h2>
<p>You can be overloaded with the different data types for index. The following example overloads an indexer with int type index as well as string type index.</p>
<div>
    <div>Example: Override Indexer</div>
    <div>
        <pre><code>class StringDataStore
{
    private string[] strArr = new string[10]; // internal data storage

    // int type indexer
    public string this[int index]
    {
        get
        {
            if (index &lt; 0 || index &gt;= strArr.Length)
                throw new IndexOutOfRangeException(&quot;Index out of range&quot;);

            return strArr[index];
        }

        set
        {
            if (index &lt; 0 || index &gt;= strArr.Length)
                throw new IndexOutOfRangeException(&quot;Index out of range&quot;);

            strArr[index] = value;
        }
    }

    // string type indexer
    public string this[string name]
    {
        get
        {
            foreach (string str in strArr){
                if(str.ToLower() == name.ToLower())        
                    return str;
                }
                    
            return null;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        StringDataStore strStore = new StringDataStore();

        strStore[0] = &quot;One&quot;;
        strStore[1] = &quot;Two&quot;;
        strStore[2] = &quot;Three&quot;;
        strStore[3] = &quot;Four&quot;;
        
        Console.WriteLine(strStore[&quot;one&quot;]);
        Console.WriteLine(strStore[&quot;two&quot;]);
        Console.WriteLine(strStore[&quot;Three&quot;]);
        Console.WriteLine(strStore[&quot;Four&quot;]);
    }
}
</code></pre>
    </div>
    <div><a href="https://www.tutorialsteacher.com/codeeditor?cid=cs-SDt7cX" target="_blank" title="Try this example code yourself">Try it</a></div>
    <p>Reference:<a href="https://www.tutorialsteacher.com/csharp/csharp-indexer">Indexers, Generic Indexer, Overload Indexers in C# (tutorialsteacher.com)</a>&nbsp;</p>
</div>
