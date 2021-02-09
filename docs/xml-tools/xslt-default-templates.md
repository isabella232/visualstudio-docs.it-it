---
title: Modelli XSLT predefiniti
description: Informazioni sui modelli XSLT predefiniti che vengono usati durante l'elaborazione XSLT quando non esiste una regola di modello esplicita corrispondente nel foglio di stile.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 74b4cfebc7a6160577f1e817c9171f2eae69533c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874756"
---
# <a name="xslt-default-templates"></a>Modelli predefiniti XSLT

Se il foglio di stile non contiene corrispondenti regole di modello esplicite, nel corso dell'elaborazione XSLT viene usato un modello predefinito. Il modello predefinito, noto anche come regola di modello incorporata, è definito nella sezione 5.8 della raccomandazione W3C XSLT 1.0 (informazioni in lingua inglese). Il modello predefinito consente al processore XSLT di elaborare un nodo anche in assenza di corrispondenti regole di modello esplicite. Tuttavia, poiché la regola di modello incorporata non è definita in modo esplicito nel foglio di stile, possono verificarsi trasformazioni XSLT impreviste o ambigue.

Il debugger XSLT visualizza il codice dei modelli XSLT predefiniti. Nel corso di una trasformazione XSLT il modello predefinito eventualmente usato viene visualizzato in una finestra del debugger. Ciò consente di eseguire il codice del modello e di impostare punti di interruzione nelle relative istruzioni.

## <a name="see-also"></a>Vedi anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
