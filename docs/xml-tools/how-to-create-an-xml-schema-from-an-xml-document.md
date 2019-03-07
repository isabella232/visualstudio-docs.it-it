---
title: Creare uno Schema XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526129"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedura: Creare uno schema XML da un documento XML

L'editor XML consente di creare uno schema di XML Schema definition language (XSD) da un documento XML. Il file XML determina la modalità di generazione dello schema nel modo seguente:

- Se al documento XML non è associato alcuno schema o DTD (Document Type Definition), i dati del documento XML vengono usati per inferire un nuovo schema XML.

- Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.

- Se il documento XML contiene uno schema XDR (XML-Data Reduced) inline, lo schema XDR viene convertito in uno schema XML corrispondente.

Gli schemi creati vengono quindi utilizzati per fornire funzionalità IntelliSense per il file XML.

Per altre informazioni sul motore di inferenza dello schema, vedere [inferire uno schema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Per creare uno schema XML

1. Aprire un file XML in Visual Studio.

2. Nella barra dei menu, scegliere **XML** > **Create Schema**.

   Un documento XML Schema viene creato e aperto per ogni spazio dei nomi disponibile nel file XML. Ogni schema viene aperto come file esterno temporaneo. Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)