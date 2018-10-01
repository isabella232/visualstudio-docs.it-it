---
title: Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18524cb3b27a05763187b9d5567d127af39c25d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527821"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [pagina delle opzioni, i tipi di carattere e colori nodo proprietà](https://docs.microsoft.com/visualstudio/ide/reference/options-page-fonts-and-colors-node-properties).  
  
  
Questo documento descrive le proprietà di tipi di carattere e colori per una finestra degli strumenti registrata per la visualizzazione in **Tipi di carattere e colori** nella categoria **Ambiente** della finestra di dialogo **Opzioni**. Supporta la natura dinamica dei gruppi di elementi colorabili, che possono cambiare se vengono installati o disinstallati pacchetti VSPackage.  
  
 La sezione seguente illustra un esempio di un tipo di finestra registrata e le proprietà disponibili per ogni finestra.  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor di testo o Stampante o Finestre di dialogo e degli strumenti  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 oppure  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 oppure  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nome degli elementi delle proprietà|Valore|Descrizione|  
|------------------------|-----------|-----------------|  
|FontFamily|Get/Set (String)|Il tipo di carattere da usare, ad esempio "Courier New".|  
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>) |Valore <xref:EnvDTE.vsFontCharSet> che specifica il tipo di set di caratteri da usare, ad esempio ebraico o russo. |  
|FontSize|Get/Set (Short)|La dimensione del carattere da usare, in punti. Ad esempio, 10 o 12.|  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo delle impostazioni relative alle opzioni](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Determinazione dei nomi degli elementi delle proprietà nelle pagine delle opzioni](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Pagina delle opzioni, Proprietà del nodo Ambiente](../../ide/reference/options-page-environment-node-properties.md)   
 [Pagina delle opzioni, Proprietà del nodo Editor di testo](../../ide/reference/options-page-text-editor-node-properties.md)



