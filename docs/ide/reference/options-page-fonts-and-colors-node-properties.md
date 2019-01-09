---
title: Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61b36afc1098a5045bfefcb92fb2a3fda36d81ca
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938695"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Pagina delle opzioni, Proprietà del nodo Tipi di carattere e colori
Questo documento descrive le proprietà di tipi di carattere e colori per una finestra degli strumenti registrata per la visualizzazione in **Tipi di carattere e colori** nella categoria **Ambiente** della finestra di dialogo **Opzioni**. Supporta la natura dinamica dei gruppi di elementi colorabili, che possono cambiare se vengono installati o disinstallati pacchetti VSPackage.

 La sezione seguente illustra un esempio di un tipo di finestra registrata e le proprietà disponibili per ogni finestra.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor di testo o Stampante o Finestre di dialogo e degli strumenti
 `DTE.Properties("FontsAndColors", "TextEditor")`

 oppure

 `DTE.Properties("FontsAndColors", "Printer")`

 -oppure-

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nome degli elementi delle proprietà|Value|Description|
| - |-----------|-----------------|
|FontFamily|Get/Set (String)|Il tipo di carattere da usare, ad esempio "Courier New".|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>) |Valore <xref:EnvDTE.vsFontCharSet> che specifica il tipo di set di caratteri da usare, ad esempio ebraico o russo. |
|FontSize|Get/Set (Short)|La dimensione del carattere da usare, in punti. Ad esempio, 10 o 12.|

## <a name="see-also"></a>Vedere anche

- [Controllo delle impostazioni relative alle opzioni](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Determinazione dei nomi degli elementi delle proprietà nelle pagine delle opzioni](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Pagina delle opzioni, Proprietà del nodo Ambiente](../../ide/reference/options-page-environment-node-properties.md)
- [Pagina delle opzioni, Proprietà del nodo Editor di testo](../../ide/reference/options-page-text-editor-node-properties.md)