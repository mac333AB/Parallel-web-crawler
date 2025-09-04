## 🕸️ Parallel Web Crawler

A multi-threaded web crawler built in Java that parses and analyzes web pages to extract popular words and measure performance.
This project is an enhancement of a legacy single-threaded crawler, upgraded to leverage parallelism with ForkJoinPool for faster throughput.

# 🚀 Features

Parallel crawling using ForkJoinPool.

Configurable JSON settings (start pages, max depth, timeout, ignored words/URLs, parallelism level, etc.).

Result output in JSON including:

Word frequency count (top N popular words).

Number of unique URLs visited.

Performance profiling with execution time for annotated methods.

Functional word counting using Java Streams (no loops).

# ⚙️ Tech Stack

Java 17

Maven (build tool)

Jackson (JSON parsing & writing)

Jsoup (HTML parsing)

JUnit 5 & Truth (unit testing)

Guice (dependency injection)

# 📂 Project Structure
src/
 ├── main/java/com/udacity/webcrawler/
 │    ├── json/                # JSON config & result handling
 │    ├── parser/              # Page parsing logic
 │    ├── profiler/            # Method profiling utilities
 │    ├── main/                # Entry point (WebCrawlerMain.java)
 │    ├── SequentialWebCrawler # Legacy single-threaded crawler
 │    └── ParallelWebCrawler   # New parallel crawler
 └── test/java/com/udacity/webcrawler/
      └── ... (JUnit tests)

# 🛠️ Setup & Run
Prerequisites

Java JDK 17+

Maven 3.6.3+

Build
mvn clean package

Run (Legacy Sequential Crawler)
java -classpath target/udacity-webcrawler-1.0.jar \
    com.udacity.webcrawler.main.WebCrawlerMain \
    src/main/config/sample_config_sequential.json

Run (Parallel Crawler)
java -classpath target/udacity-webcrawler-1.0.jar \
    com.udacity.webcrawler.main.WebCrawlerMain \
    src/main/config/sample_config.json

# 🧪 Running Tests
# Run all tests
mvn test

# Run specific test
mvn test -Dtest=WebCrawlerTest

# 📊 Example Output

Crawl Result (crawlResults.json)

{
  "wordCounts": {
    "crawler": 12,
    "java": 8,
    "parallel": 5
  },
  "urlsVisited": 15
}


Profiler Output (profileData.txt)

Run at Tue, 02 Sep 2025 18:45:21 GMT
com.udacity.webcrawler.ParallelWebCrawler#crawl took 0m 1s 412ms
com.udacity.webcrawler.parser.PageParserImpl#parse took 0m 2s 38ms

#📌 Learning Outcomes

Implemented builder pattern with Jackson for config handling.

Used ForkJoinPool for recursive parallelism.

Designed thread-safe data structures for concurrent crawling.

Applied functional programming (Java Streams) for word counting.

Built a custom profiler using dynamic proxies & annotations.

#📄 License

This project is open-source under the MIT License.

✨ Built with Java, concurrency, and a love for clean code.