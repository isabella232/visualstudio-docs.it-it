---
title: Codifiche e interruzioni di riga | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fd03dba0dfb13723fcb44d489a7b850aebeb1e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528152"
---
# <a name="encodings-and-line-breaks"></a>Codifiche e interruzioni di riga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [codifiche e interruzioni di riga](https://docs.microsoft.com/visualstudio/ide/encodings-and-line-breaks).  
  
In Visual Studio è possibile usare le impostazioni **File/Opzioni di salvataggio avanzate** per determinare il tipo di caratteri dell'interruzione di riga. Con le stesse impostazioni è anche possibile modificare la codifica di un file.  
  
> [!NOTE]
>  Se si usano determinati tipi di impostazioni di sviluppo (Visual Basic, F #, sviluppo Web), l'impostazione **Opzioni di salvataggio avanzate** potrebbe non essere visualizzata nel menu. Per modificare le impostazioni (ad esempio in Generale), aprire **Strumenti / Importa ed Esporta impostazioni**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In Visual Studio i caratteri seguenti vengono interpretati come interruzioni di riga:  
  
-   CRLF: ritorno a capo + avanzamento riga, caratteri Unicode 000D + 000A  
  
-   LF: avanzamento riga, carattere Unicode 000A  
  
-   NEL:rRiga successiva, carattere Unicode 0085  
  
-   LF: separatore di riga, carattere Unicode 2028  
  
-   PS: separatore di paragrafo, carattere Unicode 2029  
  
 Il testo che viene copiato da altre applicazioni mantiene la codifica e i caratteri originali dell'interruzione di riga. Ad esempio, quando il testo viene copiato da Blocco note e incollato in un file di testo in Visual Studio, il testo mantiene le stesse impostazioni che aveva in Blocco note.  
  
 Quando si apre un file con caratteri diversi dell'interruzione di riga, è possibile che venga visualizzata una finestra di dialogo in cui si chiede se normalizzare i caratteri dell'interruzione di riga incoerenti e quale tipo di interruzione di riga scegliere.



