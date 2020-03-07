# Challenge 1

Create a watcher that reads all .txt files uploaded to a folder and writes its contents to files in another folder.

The main file of the application must be called main.py and it must receive two arguments, src_folder and dst_folder.

- src_folder: the full path to the folder that will be monitored
- dst_folder: the full path to the destination folder, where the content will be written

Usage example:

```
python  main.py /home/biga/Downloads /home/biga/destination
```

This will monitor all files uploaded to Downloads and copy the content of the .txt files to the destination folder.

# Requirements

- All code must be in github
- If the path given in the arguments does not exist, an error message should be thrown saying it does not exist. 
- If the number of arguments is different from 2, an error message should be thrown specifying the error
- The files in the destination folder must be named file_1.txt, file_2.txt … file_n.txt, where n is the n-th - uploaded file.
- The valid .txt files will have a header, it must be checked and matched to validate the file. See below for more details.

# Header

All valid .txt files will start with these lines:

```
header_size: 72
meaning_of_life: 42
necessary_this_really_is?: no
content_length: SOME_NUMBER
```

- If meaning_of_life is not 42 the file should be refused;
- The file should be accepted regardless  necessary_this_really_is? exists or not;
- content_length must exist, it specifies the content length that shall be copied to the other file. So it must be an integer number. If content_length does not exist or SOME_NUMBER is not an integer, the file must be refused.
- header_size specifies the size of the header without counting white spaces and new lines
- If header_size does not exist or its value is not an integer the file must be ignored
- The first new line after content_length will always be "\n" and is to be ignored


## Examples

Some examples of valid files 
### Carry_on.txt
```
header_size: 63
meaning_of_life: 42
necessary_this_really_is?: no
content_length: 12

Carry on my wayward son, there will be peace when you are gone
```

This file is valid and only the first 12 characters, "Carry on my " should be copied to a file named file_1.txt

### Homops.txt

```
Header_size: 36
Meaning_of_life: 42
Content_length: 100

Homops
```

This file is also valid and "Homops" should be copied to a file named file_2.txt
