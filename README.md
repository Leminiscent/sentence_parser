# Sentence Parser

This Python script is designed to parse sentences using the Natural Language Toolkit (NLTK) based on a defined grammar of terminals and non-terminals. It leverages NLTK's Context-Free Grammar (CFG) and Chart Parsing algorithm to identify the structure of sentences and extract noun phrase chunks.

## Features

- Parses input sentences to identify grammatical structure.
- Extracts and displays noun phrase chunks.
- Utilizes a custom context-free grammar for parsing.
- Can read sentences from a file or user input.
- Prints each parse tree and the noun phrase chunks it contains.

## Requirements

- Python 3.x
- NLTK library

## Setup

Before running the script, ensure you have Python 3.x installed on your system and install the NLTK library using pip:

```
pip install nltk
```

## Usage

To use the script, you can either provide a sentence as input directly or specify a filename as an argument to read the sentence from a file.

- **Direct Input:**

  Simply run the script without any arguments:

```
python sentence_parser.py
```

When prompted, enter your sentence.

- **From File:**

Run the script with the filename as an argument:

```
python sentence_parser.py sentence_file.txt
```

Replace `sentence_file.txt` with the path to your file containing the sentence.

## Grammar

The script defines a set of terminals and non-terminals as part of its grammar. Terminals include various parts of speech such as adjectives, adverbs, conjunctions, determiners, nouns, prepositions, and verbs. Non-terminals define the sentence structure, including noun phrases (NP), verb phrases (VP), adjective phrases (AdjP), and prepositional phrases (PP).

## Functions

- `main()`: The main function of the script. It reads the sentence input and attempts to parse it.
- `preprocess(sentence)`: Processes the input sentence by tokenizing and converting it to lowercase.
- `np_chunk(tree)`: Extracts noun phrase chunks from the parse tree.

## Example

Here's a simple example sentence to try with the script:

```
I had a little moist red paint in the palm of my hand.
```

After processing, the script will output the parse tree(s) and the noun phrase chunks identified within the sentence:

```
              S                                                       
  ____________|______________________                                  
 |                                   VP                               
 |    _______________________________|_________________________        
 |   |                         NP                              |      
 |   |                _________|__________________             |       
 |   |               NP                   |       |            |      
 |   |    ___________|_______________     |       |            |       
 |   |   |          AdjP             |    |       |            |      
 |   |   |     ______|____           |    |       |            |       
 |   |   |    |          AdjP        |    |       |            |      
 |   |   |    |       ____|____      |    |       |            |       
 NP  |   |    |      |        AdjP   |    |       NP           PP     
 |   |   |    |      |         |     |    |    ___|___      ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det      N    P  Det  N  
 |   |   |    |      |         |     |    |   |       |    |   |   |   
 i  had  a  little moist      red  paint  in the     palm  of  my hand

Noun Phrase Chunks
i
a little moist red paint
the palm
              S                                                   
  ____________|______________________                              
 |                                   VP                           
 |    _______________________________|____________                 
 |   |               NP                           |               
 |   |    ___________|_______________             |                
 |   |   |          AdjP             |            PP              
 |   |   |     ______|____           |     _______|____            
 |   |   |    |          AdjP        |    |            NP         
 |   |   |    |       ____|____      |    |    ________|___        
 NP  |   |    |      |        AdjP   |    |   |   |        PP     
 |   |   |    |      |         |     |    |   |   |     ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det  N    P  Det  N  
 |   |   |    |      |         |     |    |   |   |    |   |   |   
 i  had  a  little moist      red  paint  in the palm  of  my hand

Noun Phrase Chunks
i
a little moist red paint
the palm of my hand
              S                                                       
  ____________|______________________                                  
 |                                   VP                               
 |    _______________________________|____________                     
 |   |               NP                           PP                  
 |   |    ___________|_______________      _______|____                
 |   |   |          AdjP             |    |            NP             
 |   |   |     ______|____           |    |    ________|___            
 |   |   |    |          AdjP        |    |   |   |        PP         
 |   |   |    |       ____|____      |    |   |   |     ___|___        
 NP  |   |    |      |        AdjP   |    |   |   |    |       NP     
 |   |   |    |      |         |     |    |   |   |    |    ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det  N    P  Det      N  
 |   |   |    |      |         |     |    |   |   |    |   |       |   
 i  had  a  little moist      red  paint  in the palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
my hand
              S                                                           
  ____________|______________________                                      
 |                                   VP                                   
 |    _______________________________|________________                     
 |   |               NP                               |                   
 |   |    ___________|_______________                 |                    
 |   |   |          AdjP             |                PP                  
 |   |   |     ______|____           |     ___________|____                
 |   |   |    |          AdjP        |    |                NP             
 |   |   |    |       ____|____      |    |        ________|_______        
 NP  |   |    |      |        AdjP   |    |       NP       |       NP     
 |   |   |    |      |         |     |    |    ___|___     |    ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det      N    P  Det      N  
 |   |   |    |      |         |     |    |   |       |    |   |       |   
 i  had  a  little moist      red  paint  in the     palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
the palm
my hand
              S                                                           
  ____________|______________________                                      
 |                                   VP                                   
 |    _______________________________|_________________________            
 |   |                         NP                              |          
 |   |                _________|__________________             |           
 |   |               NP                   |       |            |          
 |   |    ___________|_______________     |       |            |           
 |   |   |          AdjP             |    |       |            |          
 |   |   |     ______|____           |    |       |            |           
 |   |   |    |          AdjP        |    |       |            PP         
 |   |   |    |       ____|____      |    |       |         ___|___        
 NP  |   |    |      |        AdjP   |    |       NP       |       NP     
 |   |   |    |      |         |     |    |    ___|___     |    ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det      N    P  Det      N  
 |   |   |    |      |         |     |    |   |       |    |   |       |   
 i  had  a  little moist      red  paint  in the     palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
the palm
my hand
              S                                                   
  ____________|______________________                              
 |                                   VP                           
 |    _______________________________|____                         
 |   |                                    NP                      
 |   |                ____________________|____________            
 |   |               NP                   |            |          
 |   |    ___________|_______________     |            |           
 |   |   |          AdjP             |    |            |          
 |   |   |     ______|____           |    |            |           
 |   |   |    |          AdjP        |    |            NP         
 |   |   |    |       ____|____      |    |    ________|___        
 NP  |   |    |      |        AdjP   |    |   |   |        PP     
 |   |   |    |      |         |     |    |   |   |     ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det  N    P  Det  N  
 |   |   |    |      |         |     |    |   |   |    |   |   |   
 i  had  a  little moist      red  paint  in the palm  of  my hand

Noun Phrase Chunks
i
a little moist red paint
the palm of my hand
              S                                                       
  ____________|______________________                                  
 |                                   VP                               
 |    _______________________________|____                             
 |   |                                    NP                          
 |   |                ____________________|____________                
 |   |               NP                   |            |              
 |   |    ___________|_______________     |            |               
 |   |   |          AdjP             |    |            NP             
 |   |   |     ______|____           |    |    ________|___            
 |   |   |    |          AdjP        |    |   |   |        PP         
 |   |   |    |       ____|____      |    |   |   |     ___|___        
 NP  |   |    |      |        AdjP   |    |   |   |    |       NP     
 |   |   |    |      |         |     |    |   |   |    |    ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det  N    P  Det      N  
 |   |   |    |      |         |     |    |   |   |    |   |       |   
 i  had  a  little moist      red  paint  in the palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
my hand
              S                                                           
  ____________|______________________                                      
 |                                   VP                                   
 |    _______________________________|____                                 
 |   |                                    NP                              
 |   |                          __________|________________________        
 |   |                         NP                          |       |      
 |   |                _________|__________________         |       |       
 |   |               NP                   |       |        |       |      
 |   |    ___________|_______________     |       |        |       |       
 |   |   |          AdjP             |    |       |        |       |      
 |   |   |     ______|____           |    |       |        |       |       
 |   |   |    |          AdjP        |    |       |        |       |      
 |   |   |    |       ____|____      |    |       |        |       |       
 NP  |   |    |      |        AdjP   |    |       NP       |       NP     
 |   |   |    |      |         |     |    |    ___|___     |    ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det      N    P  Det      N  
 |   |   |    |      |         |     |    |   |       |    |   |       |   
 i  had  a  little moist      red  paint  in the     palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
the palm
my hand
              S                                                           
  ____________|______________________                                      
 |                                   VP                                   
 |    _______________________________|____                                 
 |   |                                    NP                              
 |   |                ____________________|________________                
 |   |               NP                   |                |              
 |   |    ___________|_______________     |                |               
 |   |   |          AdjP             |    |                |              
 |   |   |     ______|____           |    |                |               
 |   |   |    |          AdjP        |    |                NP             
 |   |   |    |       ____|____      |    |        ________|_______        
 NP  |   |    |      |        AdjP   |    |       NP       |       NP     
 |   |   |    |      |         |     |    |    ___|___     |    ___|___    
 N   V  Det  Adj    Adj       Adj    N    P  Det      N    P  Det      N  
 |   |   |    |      |         |     |    |   |       |    |   |       |   
 i  had  a  little moist      red  paint  in the     palm  of  my     hand

Noun Phrase Chunks
i
a little moist red paint
the palm
my hand
```
