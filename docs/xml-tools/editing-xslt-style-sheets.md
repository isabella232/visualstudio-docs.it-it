---
title: Modifica di fogli di stile XSLT
description: Informazioni sulle funzionalità dell'editor XML per la modifica dei fogli di stile XSLT, incluse la colorazione della sintassi, le sottolineature e l'avvio del debugger XSLT dall'editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31d961de62822bf036a898601ba0125db5a0dafc
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045877"
---
# <a name="edit-xslt-style-sheets"></a>Modifica dei fogli di stile XSLT

È inoltre possibile utilizzare l'editor XML per modificare i fogli di stile XSLT. È possibile usare le funzionalità predefinite dell'editor, quali IntelliSense, struttura, frammenti XML e così via. Sono inoltre disponibili nuove funzionalità che semplificano lo sviluppo in XSLT.

## <a name="xslt-features"></a>Funzionalità XSLT

Nella tabella seguente vengono descritte le funzionalità specifiche per usare i fogli di stile XSLT.

**Colorazione della sintassi**

Le parole chiave XSLT, ad esempio `template` e `match` , vengono visualizzate nel colore della parola chiave XSLT specificato dalle impostazioni relative ai **tipi di carattere e ai colori** .

**Sottolineature ondulate**

Nell'editor XML viene utilizzato il file *XSLT. xsd* installato per convalidare i fogli di stile XSLT. Gli errori di convalida vengono visualizzati con una sottolineatura ondulata di colore blu. L'editor XML compila inoltre il foglio di stile in background e segnala gli errori o gli avvisi del compilatore con sottolineature ondulate appropriate.

**Supporto per i blocchi di script**

Il codice nei blocchi di script è supportato dal debugger XSLT, consentendo di impostare punti di interruzione e di eseguire il codice del blocco di script.

**Visualizzazione dell'output XSLT**

È possibile eseguire una trasformazione XSL e visualizzare l'output dell'editor XML. Per ulteriori informazioni, vedere [procedura: eseguire una trasformazione XSLT dall'editor XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Debug XSLT**

È possibile avviare il debugger XSLT da un file XSLT nell'editor XML. Il debugger supporta l'impostazione dei punti di interruzione nel file XSLT, la visualizzazione dello stato di esecuzione di XSLT e così via. Se si passa con il mouse su una variabile XSLT, viene visualizzata una descrizione con il valore della matrice. Il debugger può essere usato per eseguire il debug di un foglio di stile o di una trasformazione XSLT chiamata da un'altra applicazione. Per ulteriori informazioni, vedere [debug di XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
