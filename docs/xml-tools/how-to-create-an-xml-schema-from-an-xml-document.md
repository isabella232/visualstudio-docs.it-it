---
title: Creazione di uno schema XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73563d732aab48192892794c15750bc9e5d3eb6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645958"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedura: creare un XML Schema da un documento XML

L'editor XML consente di creare uno schema XSD (XML Schema Definition Language) da un documento XML. Il file XML determina il modo in cui viene generato lo schema nel modo seguente:

- Se al documento XML non è associato alcuno schema o DTD (Document Type Definition), i dati del documento XML vengono usati per inferire un nuovo schema XML.

- Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.

- Se il documento XML contiene uno schema XDR (XML-Data Reduced) inline, lo schema XDR viene convertito in uno schema XML corrispondente.

Gli schemi creati vengono quindi utilizzati per fornire IntelliSense per il file XML.

Per ulteriori informazioni sul motore di inferenza dello schema, vedere [dedurre un XML Schema](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Per creare uno schema XML

1. Aprire un file XML in Visual Studio.

2. Nella barra dei menu scegliere **XML**  > **Crea schema**.

   Un documento XML Schema viene creato e aperto per ogni spazio dei nomi trovato nel file XML. Ogni schema viene aperto come file esterno temporaneo. Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)