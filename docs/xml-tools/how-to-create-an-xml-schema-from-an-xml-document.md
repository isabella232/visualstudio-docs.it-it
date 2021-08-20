---
title: Creare uno schema XML
description: Informazioni su come usare l'editor XML in Visual Studio per creare uno schema XSD (XML Schema Definition Language) da un documento XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: eba93ba429394272402c89e427ad974d1c9eb0f8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130208"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procedura: Creare uno schema XML da un documento XML

L'editor XML consente di creare uno schema XSD (XML Schema Definition Language) da un documento XML. Il file XML determina come viene generato lo schema nel modo seguente:

- Se al documento XML non è associato alcuno schema o DTD (Document Type Definition), i dati del documento XML vengono usati per inferire un nuovo schema XML.

- Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.

- Se il documento XML contiene uno schema XDR (XML-Data Reduced) inline, lo schema XDR viene convertito in uno schema XML corrispondente.

Gli schemi creati vengono quindi usati per fornire IntelliSense per il file XML.

Per altre informazioni sul motore di inferenza dello schema, vedere [Infer an XML Schema](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Per creare uno schema XML

1. Aprire un file XML in Visual Studio.

2. Sulla barra dei menu scegliere **XML**  >  **Create Schema**.

   Viene creato e aperto un documento XML Schema per ogni spazio dei nomi presente nel file XML. Ogni schema viene aperto come file esterno temporaneo. Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.

## <a name="see-also"></a>Vedi anche

- [Editor XML](../xml-tools/xml-editor.md)
