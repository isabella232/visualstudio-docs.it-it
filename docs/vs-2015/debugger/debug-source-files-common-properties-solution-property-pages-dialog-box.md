---
title: Origine file, proprietà comuni, soluzione dialogo Pagine delle proprietà di debug | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b94306c44b8a19d1fbf924fe361d317dd911110b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519220"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [file di origine eseguire il Debug, proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione](https://docs.microsoft.com/visualstudio/debugger/debug-source-files-common-properties-solution-property-pages-dialog-box).  
  
In questa pagina delle proprietà è specificato il punto in cui il debugger cerca i file di origine durante il debug della soluzione.  
  
 Per l'accesso di **Esegui Debug dei file di origine** pagina delle proprietà, pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e selezionare **proprietà** dal menu di scelta rapida. Espandere la **proprietà comuni** cartella e scegliere il **Esegui Debug dei file di origine** pagina.  
  
 **Directory contenenti codice sorgente**  
 Contiene un elenco di directory in cui il debugger cerca i file di origine durante il debug della soluzione. La ricerca viene eseguita anche nelle sottodirectory delle directory specificate.  
  
 **Non cerca i file di origine**  
 Immettere i nomi dei file che non si desidera vengano letti dal debugger. Se il debugger trova uno di questi file in una delle directory specificate in precedenza, lo ignora. Se il **Trova origine** finestra di dialogo viene visualizzata anche se si esegue il debug e, si fa clic su **Annulla**, il file cercato verrà aggiunto a questo elenco in modo che il debugger non può continuare la ricerca per tale file.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)



