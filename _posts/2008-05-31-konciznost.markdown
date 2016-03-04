---
layout: post
title: Konciznost
date: '2008-05-31 12:41:07 +0200'
mt_id: 228
post_id: 228
author: jablan
---
Čitanje tekst fajla u string.

U Javi:

    File aFile = new File("/home/jablan/blah.txt");
    StringBuffer contents = new StringBuffer();
        
    try {
      BufferedReader input = new BufferedReader(new FileReader(aFile));
      try {
        String line = null;
        while (( line = input.readLine()) != null){
          contents.append(line);
          contents.append(System.getProperty("line.separator"));
        }
      }
      finally {
        input.close();
      }
    }
    catch (IOException ex){
      ex.printStackTrace();
    }
    
    return contents.toString();

U Rubiju:

    return File.read('/home/jablan/blah.txt')

:D

