---
title: 'Procedura: creare una. File Vsct da un oggetto esistente. File CTO | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: e77ebf34cd56cee80040009cff3ebb2fee9befac
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590598"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedura: Creare un file con estensione vsct da un file CTO esistente
È possibile creare un file con estensione vsct basato su XML da un file CTO binario esistente. Questa operazione consente di sfruttare il nuovo formato di compilatore della tabella comandi. Questo processo funziona anche se il file CTO è stato compilato da un file CTC. È possibile modificare e compilare il file VSCT in un altro file CTO.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Per creare un file con estensione vsct da un file CTO  
  
1.  Ottenere copie del file CTO e del corrispondente file CTSYM.  
  
2.  Inserire i file nella stessa directory del compilatore vsct.exe.  
  
3.  Nel prompt dei comandi di Visual Studio, passare alla directory che contiene i file con estensione cto e ctsym.  
  
4.  Tipo di **vsct.exe** _ctofilename_**CTO** _vsctfilename_**vsct -S**  _symfilename_**ctsym**.  
  
     `ctofilename` è il nome del file CTO `vsctfilename` è il nome del file vsct che si desidera creare, e `symfilename` è il nome del file ctsym.  
  
     Questo processo crea un nuovo file del compilatore della tabella comandi XML con estensione vsct. È possibile modificare e compilare il file con vsct.exe, il compilatore vsct, come si farebbe con qualsiasi altro file VSCT.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare una. File Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)