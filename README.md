# LearnProgrammingBot
LearnProgrammingBot is a bot for [reddit](https://reddit.com) that uses
scikit-learn and supervised learning techniques to categorise submissions and
reply with useful and appropriate links.

It is intended to answer common questions on /r/learnprogramming that can
be found on the wiki, but in theory it should be suitable for any subreddit
provided that it is trained properly. The default training set should be fine
for most programming subreddits, but it can be extended at any time.

## Installation
LearnProgrammingBot requires scikit-learn, praw and sqlalchemy. Due to this, the
installation instructions are slightly different depending on which platform you
are using. It *should* work with both Python 2 and Python 3 (unit tests are
coming soon)

Before continuing, download the code (either through the source zip or releases
tab) and extract it if necessary, or clone using git. Then, open a command
prompt or terminal and `cd` to the directory where you have extracted the code.

### Windows
As an administrator, in the command prompt, run:

    pip install -r requirements.txt

### Mac

    sudo pip install -r requirements.txt

### Debian/Ubuntu/Mint

    sudo apt-get install python-scipy
    sudo pip install sqlalchemy scikit-learn praw

## Setup and Running
You'll need to enter a few variables into `settings.py`. Just follow the
instructions on lines preceded by # (comments) and fill in the correct data.

To run, use `./main.py run` in the terminal. This will run continuously until
killed using Ctrl+C or an exception. You might find useful logging information
in bot.log if the bot does crash. Feel free to report an issue if you do find a
bug!

## Classifications
Currently, the classifier only recognises 3 types of post classes:

- 'good' - the post is a good question for /r/learnprogramming
- 'faq' - the post contains a common question that is probably on the FAQ
- 'bad' - the post is formatted badly, off topic or does not contain enough
detail.

## Accuracy
As of commit `4c60f73`, the classifier's accuracy is as follows:

- Correct classification = 73%
- False negative = 17%
- False positive = 7%
- Wrong category = 3%

False negatives are counted as any time that the actual class was not 'good' and
the classifier returned 'good'. False positives occur when the actual class was
'good' but the classifer did not return 'good'. Wrong category classifications
occur when the classifier returned a different negative classification (i.e.
'faq' instead of 'bad')

## Roadmap and Planned Features
- Unit tests
- More modular approach so that extra modules can be installed to make the bot
more customisable.

## Contributing
We're happy to accept contributors - you don't need to be an expert, just file
an issue about getting started and we can start there!

## License

MIT License. Please see the LICENSE file!
