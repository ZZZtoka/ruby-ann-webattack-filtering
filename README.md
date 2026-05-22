# ruby-ann-webattack-filtering

A proof-of-concept project to detect and filter SQL Injection and XSS 
web attacks using an Artificial Neural Network (ANN) in Ruby.

## How It Works

The system uses a Bag of Words model to convert HTTP request strings 
into feature vectors, which are then classified by a neural network 
as either Normal or Abnormal (attack) traffic.

The pipeline:
1. HTTP traffic logs are loaded from `data/` directory
2. A Bag of Words model tokenizes and normalizes the request strings
3. A neural network is trained on labeled normal and abnormal traffic
4. The trained model classifies new HTTP requests in real time

## Requirements

- Ruby 2.0+
- Gems: `stopwords`, `fast_stemmer`, `narray`, `colorize`

Install dependencies:
```bash
gem install stopwords fast_stemmer narray colorize
```

## Usage

```bash
ruby ann.rb
```

The script will:
- Load training data from `data/abnormal_http_traffic.txt` 
  and `data/normal_http_traffic.txt`
- Train the neural network (or load a saved model from `/tmp/ann.db`)
- Output classification accuracy on the test set
- Save the trained model for future use

## Project Structure
├── ann.rb                          # Main entry point
├── lib/
│   ├── rann.rb                     # Neural network implementation (RPROP)
│   └── bag_of_words.rb             # Bag of Words feature extraction
├── data/
│   ├── abnormal_http_traffic.txt   # Labeled attack traffic samples
│   └── normal_http_traffic.txt     # Labeled normal traffic samples
└── README.md

## Attack Types in Dataset

The abnormal traffic dataset includes various SQL injection 
and XSS attack patterns such as:
- Boolean-based SQL injection (`AND 1=1`, `OR 'a'='a'`)
- Time-based blind SQL injection (`SLEEP(5)`, `WAITFOR DELAY`)
- Union-based SQL injection (`UNION ALL SELECT NULL`)
- Error-based SQL injection (`CONVERT`, `CAST`, `XMLType`)
- Cookie and header injection attempts

## Credits

- Neural Network implementation: 
  https://github.com/gbuesing/neural-net-ruby
- Bag of Words implementation: 
  https://github.com/gbuesing/kmeans-clusterer

## License

MIT License — Copyright (c) 2015 Bar Hofesh