---
title: Input Function
keywords: vblr6.chm1011066
f1_keywords:
- vblr6.chm1011066
ms.prod: office
ms.assetid: 25ab9e37-4536-4cd0-2b29-985add94a489
ms.date: 08/28/2018
---


# Input Function

Returns [String](../../Glossary/vbe-glossary.md#string-data-type) containing characters from a file opened in **Input** or **Binary** mode.

## Syntax

**Input**(_number_, [ **#** ] _filenumber_ )
The **Input** function syntax has these parts:

### Parameters
|**Part**|**Description**|
|:-----|:-----|
| _number_|Required. Any valid [numeric expression](../../Glossary/vbe-glossary.md#numeric-expression) specifying the number of characters to return.|
| _filenumber_|Required. Any valid [file number](../../Glossary/vbe-glossary.md#file-number).|

### Return value

String

## Remarks

Data read with the **Input** function is usually written to a file with **Print #** or **Put**. Use this function only with files opened in **Input** or **Binary** mode.

Unlike the **Input #** statement, the **Input** function returns all of the characters it reads, including commas, carriage returns, linefeeds, quotation marks, and leading spaces.

With files opened for **Binary** access, an attempt to read through the file using the **Input** function until **EOF** returns **True** generates an error. Use the **LOF** and **Loc** functions instead of **EOF** when reading binary files with **Input**, or use **Get** when using the **EOF** function.

> [!NOTE]  
> Use the **InputB** function for byte data contained within text files. With **InputB**, _number_ specifies the number of bytes to return rather than the number of characters to return.


## Example

This example uses the **Input** function to read one character at a time from a file and print it to the **Immediate** window. This example assumes that `TESTFILE` is a text file with a few lines of sample data.


```vb
Dim MyChar
Open "TESTFILE" For Input As #1    ' Open file.
Do While Not EOF(1)    ' Loop until end of file.
    MyChar = Input(1, #1)    ' Get one character.
    Debug.Print MyChar    ' Print to the Immediate window.
Loop
Close #1    ' Close file.


```


