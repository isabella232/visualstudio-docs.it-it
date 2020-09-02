---
title: 'Procedura: creare un oggetto. File vsct da un esistente. File CTO | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822438"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedura: Creare un file con estensione vsct da un file CTO esistente
È possibile creare un file con estensione vsct basato su XML da un file CTO binario esistente. Questa operazione consente di sfruttare il nuovo formato di compilatore della tabella comandi. Questo processo funziona anche se il file CTO è stato compilato da un file CTC. È possibile modificare e compilare il file VSCT in un altro file CTO.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Per creare un file con estensione vsct da un file CTO  
  
1. Ottenere copie del file CTO e del corrispondente file CTSYM.  
  
2. Inserire i file nella stessa directory del compilatore vsct.exe.  
  
3. Nel prompt dei comandi di Visual Studio, passare alla directory che contiene i file con estensione cto e ctsym.  
  
4. Digitare **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct -S**_symfilename_**.ctsym**.  
  
     `ctofilename` è il nome del file CTO, `vsctfilename` è il nome del file VSCT che si vuole creare e `symfilename` è il nome del file CTSYM.  
  
     Questo processo crea un nuovo file del compilatore della tabella comandi XML con estensione vsct. È possibile modificare e compilare il file con vsct.exe, il compilatore vsct, come si farebbe con qualsiasi altro file VSCT.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un oggetto. File vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)