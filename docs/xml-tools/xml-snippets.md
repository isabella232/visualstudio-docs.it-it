---
title: frammenti XML
description: Informazioni sulla funzionalità frammenti di codice XML nell'editor XML che consente di compilare file XML più rapidamente riutilizzando frammenti di codice XML e inserendoli nei file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 3077cd59a9ab9e051a1e11e9bb1d19117cc0feb7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031848"
---
# <a name="xml-snippets"></a>frammenti XML

L'editor XML offre una funzionalità, denominata *frammenti XML,* che consente di compilare file XML più rapidamente. È possibile riutilizzare i frammenti di codice XML inserendoli nei file. È anche possibile generare dati XML in base a uno schema XSD (XML Schema Definition Language).

## <a name="reusable-xml-snippets"></a>Frammenti XML riutilizzabili

L'editor XML include molti frammenti che coprono alcune attività comuni. e che facilitano la creazione di file XML. Ad esempio, se si crea uno schema XML, l'uso dei frammenti di codice "Elemento sequenza di tipi complessi" e "Elemento tipo semplice" inserisce il testo XML seguente nel file. Il valore `name` può quindi essere modificato in base alle esigenze.

```xml
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

È possibile inserire i frammenti di codice in due modi diversi: Il **comando Inserisci frammento** di codice inserisce il frammento XML nella posizione del cursore. Il **comando Surround With** esegue il wrapping del frammento XML intorno al testo selezionato. Entrambi i comandi sono disponibili dal sottomenu **IntelliSense** nel **menu** Modifica o dal menu di scelta rapida nell'editor.

Per altre informazioni, vedere [Procedura: Usare frammenti di codice XML.](../xml-tools/how-to-use-xml-snippets.md)

## <a name="schema-generated-xml-snippets"></a>Frammenti XML generati da schema

L'editor XML ha anche la possibilità di generare un frammento di codice XML da uno schema XML. Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento. Per altre informazioni, vedere [Procedura: Generare un frammento di codice XML da uno schema XML.](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)

## <a name="create-new-xml-snippets"></a>Creare nuovi frammenti di codice XML

Oltre ai frammenti di codice inclusi in Visual Studio, è anche possibile creare e usare frammenti XML personalizzati. Per altre informazioni, vedere [Procedura: Creare frammenti di codice XML.](../xml-tools/how-to-create-xml-snippets.md)

## <a name="see-also"></a>Vedi anche

- [Frammenti di codice in Visual Studio](../ide/code-snippets.md)
- [Editor XML](../xml-tools/xml-editor.md)
