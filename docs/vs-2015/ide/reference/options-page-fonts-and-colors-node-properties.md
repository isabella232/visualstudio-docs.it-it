---
title: Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662433"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questo documento descrive le proprietà di tipi di carattere e colori per una finestra degli strumenti registrata per la visualizzazione in **Tipi di carattere e colori** nella categoria **Ambiente** della finestra di dialogo **Opzioni**. Supporta la natura dinamica dei gruppi di elementi colorabili, che possono cambiare se vengono installati o disinstallati pacchetti VSPackage.

 La sezione seguente illustra un esempio di un tipo di finestra registrata e le proprietà disponibili per ogni finestra.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor di testo o Stampante o Finestre di dialogo e degli strumenti
 `DTE.Properties("FontsAndColors", "TextEditor")`

 -oppure-

 `DTE.Properties("FontsAndColors", "Printer")`

 -oppure-

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nome degli elementi delle proprietà|Value|DESCRIZIONE|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (String)|Il tipo di carattere da usare, ad esempio "Courier New".|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Valore <xref:EnvDTE.vsFontCharSet> che specifica il tipo di set di caratteri da usare, ad esempio ebraico o russo.|
|FontSize|Get/Set (Short)|La dimensione del carattere da usare, in punti. Ad esempio, 10 o 12.|

## <a name="see-also"></a>Vedere anche
 [Controllo delle impostazioni delle opzioni](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [determinazione dei nomi degli elementi delle proprietà nella](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) pagina Opzioni pagine opzioni [, proprietà nodo ambiente](../../ide/reference/options-page-environment-node-properties.md) [pagina Opzioni, proprietà nodo Editor di testo](../../ide/reference/options-page-text-editor-node-properties.md)
