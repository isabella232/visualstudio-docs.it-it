---
title: 'Procedura: Creare uno Schema XML da un documento XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0f12436f9f129c6fb8a0fe3a4b6c853a9e58e650
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438119"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedura: di uno schema XML da un documento XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor XML consente di creare uno schema XSD (XML Schema Definition Language) da un documento XML. Il documento di istanza XML determina come viene generato lo schema nel seguente modo:  
  
- Se al documento XML non è associato alcuno schema o DTD (Document Type Definition), i dati del documento XML vengono usati per inferire un nuovo schema XML.  
  
- Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.  
  
- Se il documento XML contiene uno schema XDR (XML-Data Reduced) inline, lo schema XDR viene convertito in uno schema XML corrispondente.  
  
  Gli schemi creati vengono quindi usati per fornire IntelliSense al documento XML.  
  
  Per altre informazioni sul motore di inferenza dello schema, vedere [inferenza di uno Schema XML](http://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).  
  
### <a name="to-create-an-xml-schema"></a>Per creare uno schema XML  
  
1. Caricare un documento di istanza XML nell'editor XML.  
  
2. Fare clic sui **Create Schema** pulsante il **sulla barra degli strumenti**.  
  
     Viene creato e aperto un documento di schema XML per ogni spazio dei nomi rilevato nel documento di istanza XML. Ogni schema viene aperto come file esterno temporaneo.  
  
     Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.  
  
    > [!NOTE]
    > Il **Create Schema** comando è anche disponibile tramite il menu di scelta rapida dell'Editor XML e nel **XML** menu.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)
