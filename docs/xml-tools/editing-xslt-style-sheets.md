---
title: Modifica di fogli di stile XSLT
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f224e91f72d2fa751ddc8b170f78b8859c43f4
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548450"
---
# <a name="edit-xslt-style-sheets"></a>Modifica dei fogli di stile XSLT

L'editor XML consente anche di modificare i fogli di stile XSLT. È possibile usare le funzionalità predefinite dell'editor, quali IntelliSense, struttura, frammenti XML e così via. Sono inoltre disponibili nuove funzionalità che semplificano lo sviluppo in XSLT.

## <a name="xslt-features"></a>Funzionalità XSLT
 Nella tabella seguente vengono descritte le funzionalità specifiche per usare i fogli di stile XSLT.

 **Colorazione della sintassi**

 Parole chiave XSLT, ad esempio `template`, `match`e così via, vengono visualizzati il colore della parola chiave XSLT specificato da di **tipi di carattere e colori** impostazioni.

 **Sottolineature ondulate**

 L'Editor XML Usa installata *XSLT* file per convalidare i fogli di stile XSLT. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. L'editor XML compila inoltre il foglio di stile in background e segnala gli errori del compilatore o avvisi con le opportune sottolineature ondulate.

 **Supporto per i blocchi di script**

 Il codice nei blocchi di script è supportato dal debugger XSLT, consentendo di impostare punti di interruzione e di eseguire il codice del blocco di script.

 **Visualizzazione dell'output XSLT**

 È possibile eseguire una trasformazione XSL e visualizzare l'output dall'editor XML. Per altre informazioni, vedere [procedura: eseguire una trasformazione XSLT dall'Editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Eseguire il debug XSLT**

 È possibile avviare il debugger XSLT da un file XSLT nell'editor XML. Il debugger supporta l'impostazione dei punti di interruzione nel file XSLT, la visualizzazione dello stato di esecuzione di XSLT e così via. Se si passa con il mouse su una variabile XSLT, viene visualizzata una descrizione con il valore della matrice. Il debugger può essere usato per eseguire il debug di un foglio di stile o di una trasformazione XSLT chiamata da un'altra applicazione. Per ulteriori informazioni, vedere [debug XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)