 #  Question
 
1.Implementing a News Feed Application
  Hint: In this assignment, you will create a C# console application that demonstrates the use of delegates and events. You will create a NewsArticle class 
  that represents a news article, a NewsArticleCollection class that represents a collection of news articles, and a console application that uses the 
  NewsArticleCollection class to filter news articles by category and notify subscribers when new articles are added to or removed from the collection

# Solution

## NewsArticle.cs

```csharp
using System;
using System.Collections.Generic;
using System.Text;

namespace Day_4
{
    public class NewsArtricle
    {
        public string Title { get; set; }
        public string Category { get; set; }
        public string Content { get; set; }
        public DateTime PublishedAt { get; set; }

        public NewsArtricle(string title, string category, string content, DateTime? publishedAt = null)
        {
            Title = title;
            Category = category;
            Content = content;
            PublishedAt = publishedAt ?? DateTime.Now;
        }

        public override string ToString()
        {
            return "[" + Category + "] " + Title + " - " + Content;
        }
    }
}
```

## NewsArticleCollection.cs

```csharp
using System;
using System.Collections.Generic;
using System.Security.AccessControl;
using System.Text;

namespace Day_4
{
    public class ArticleChangedEventArgs : EventArgs
    {
        public NewsArtricle Article;
        public string Action;

        public ArticleChangedEventArgs(NewsArtricle article, string action)
        {
            Article = article;
            Action = action;
        }

    }

    public class NewsArticleCollection
    {
        private List<NewsArtricle> articles = new List<NewsArtricle>();

            //Delegate and events
            public delegate void ArticleChangedHandler(object sender, ArticleChangedEventArgs
                e);
            public event ArticleChangedHandler ArticleAdded;
            public event ArticleChangedHandler ArticleRemoved;

            //Add article
            public void AddArticle(NewsArtricle article)
            {
                articles.Add(article);

                if (ArticleAdded != null)
                {
                    ArticleAdded(this, new ArticleChangedEventArgs(article, "added"));
                }

            }

            //Remove article
            public void RemoveArticle(NewsArtricle article)
            {
                if (articles.Remove(article))
                {
                    if(ArticleRemoved != null)
                    {
                        ArticleRemoved(this, new ArticleChangedEventArgs(article, "Removed"));
                    }
                }
            }

        //Filter by category
        public List<NewsArtricle> FilterByCategory(string category)
        {
            List<NewsArtricle> result = new List<NewsArtricle>();
            foreach (var article in articles)
            {
                if (article.Category.ToLower() == category.ToLower())
                {
                    result.Add(article);
                }
            }
            return result;
        }

        //Get all articles
        public List<NewsArtricle> GetAll()
        {
            return new List<NewsArtricle>(articles);
        }

    }
}
```

## Program.cs

```csharp
namespace Day_4
{
    internal class Program
    {
        static void Main(string[] args)
        {
            NewsArticleCollection collection = new NewsArticleCollection();

            //Subscribe to events
            collection.ArticleAdded += OnArticleChanged;
            collection.ArticleRemoved += OnArticleChanged;

            //Add articles
            NewsArtricle a1 = new NewsArtricle("Tech Trends 2025", "Technology", "AI is transforming industries.");
            NewsArtricle a2 = new NewsArtricle("Sports Update", "Sports", "Local team wins championship.");
            NewsArtricle a3 = new NewsArtricle("Election Results", "Politics", "New government announced.");
     
            collection.AddArticle(a1);
            collection.AddArticle(a2);
            collection.AddArticle(a3);

            //Filter by category
            Console.WriteLine("\n--- Technology Articles ---");
            foreach(var article in collection.FilterByCategory("Technology")) 
            {
                Console.WriteLine(article);
            }

            //Remove an article
            Console.WriteLine("\n--- Removed Articles ---");
            collection.RemoveArticle(a2);

            //Show all remaining
            Console.WriteLine("\n--- All Articles ---");
            foreach (var article in collection.GetAll())
            {
                Console.WriteLine(article);
            }

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }

        // Event Handler
        private static void OnArticleChanged(object sender, ArticleChangedEventArgs e)
        {
            Console.WriteLine("[EVENT] " + e.Action + ": " + e.Article.Title);
        }
    }
}
```
