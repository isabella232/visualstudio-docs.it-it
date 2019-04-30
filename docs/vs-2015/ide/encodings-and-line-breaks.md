---
title: Codifiche e interruzioni di riga | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6ceec5e44ade219f069e72f712129a137d70875f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437530"
---
# <a name="encodings-and-line-breaks"></a>Codifiche e interruzioni di riga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile usare le impostazioni **File/Opzioni di salvataggio avanzate** per determinare il tipo di caratteri dell'interruzione di riga. Con le stesse impostazioni è anche possibile modificare la codifica di un file.  
  
> [!NOTE]
> Se si usano determinati tipi di impostazioni di sviluppo (Visual Basic, F#, sviluppo Web), l'impostazione **Opzioni di salvataggio avanzate** potrebbe non essere visualizzata nel menu. Per modificare le impostazioni (ad esempio in Generale), aprire **Strumenti / Importa ed Esporta impostazioni**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In Visual Studio i caratteri seguenti vengono interpretati come interruzioni di riga:  
  
- CRLF: Ritorno a capo + avanzamento riga, caratteri Unicode 000D + 000A  
  
- LF: Avanzamento riga, carattere Unicode 000A  
  
- NEL: Riga successiva, carattere Unicode 0085  
  
- LS: Separatore di riga, carattere Unicode 2028  
  
- PS: Separatore di paragrafo, carattere Unicode 2029  
  
  Il testo che viene copiato da altre applicazioni mantiene la codifica e i caratteri originali dell'interruzione di riga. Ad esempio, quando il testo viene copiato da Blocco note e incollato in un file di testo in Visual Studio, il testo mantiene le stesse impostazioni che aveva in Blocco note.  
  
  Quando si apre un file con caratteri diversi dell'interruzione di riga, è possibile che venga visualizzata una finestra di dialogo in cui si chiede se normalizzare i caratteri dell'interruzione di riga incoerenti e quale tipo di interruzione di riga scegliere.
