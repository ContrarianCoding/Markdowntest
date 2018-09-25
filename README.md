# Markdown example

### This is a TODO list

 - [x] complete item
 - [ ] incomplete item
 - [ ] another incomplete item

### A link to a website

[GitHub Home](https://github.com/ContrarianCoding)

### A labeled image

![Some Logo](https://ixquick-proxy.com/do/spg/show_picture.pl?l=english&rais=1&oiu=http%3A%2F%2Fallthingsd.com%2Ffiles%2F2011%2F09%2Ffree.png&sp=810387e116b895fb0130ef4c20c06af1)

### A code snippet

```python


def allcombinations(wordoptions):
	ret = [];
	if len(wordoptions) == 1:
		return wordoptions[0];
	for opt in wordoptions[0]:
		otheropts = allcombinations(wordoptions[1:]);
		for otheropt in otheropts:
			ret.append(opt + otheropt);
	return ret;


def switchchar(stri, index, character):
	wordwithone = list(stri);
	wordwithone[index] = character;
	wordwithone = ''.join(wordwithone);
	return wordwithone;

def caseoption(someword):
	opts = [];
	opts.append(someword);
	opts.append(someword.upper());
	opts.append(someword.title());
	return opts;

def wordtooptions(origword):
	opts = caseoption(origword);
	iindex = origword.find('i');
	if(iindex != -1):
		wordwithone = switchchar(origword, iindex, '1');
		wordwithexc = switchchar(origword, iindex, '!');
		opts += caseoption(wordwithone);
		opts += caseoption(wordwithexc);
		opts += wordtooptions(wordwithone);
		opts += wordtooptions(wordwithexc);
	iindex = origword.find('o');
	if(iindex != -1):
		wordwithone = switchchar(origword, iindex, '0');
		opts += caseoption(wordwithone);
		opts += wordtooptions(wordwithone);
	return opts;



nextword = "";
wordlist = [];
wordoptions = [];
while(nextword != '0'):
	nextword = raw_input("please enter next keyword or 0 to finish\n\n");
	if(nextword != '0'): wordlist.append(nextword);

for oneword in wordlist:
	wordoptions.append(wordtooptions(oneword));

totlist = allcombinations(wordoptions);

outstr = '';
for possibility in totlist:
	outstr += possibility + ',';

print outstr;

```