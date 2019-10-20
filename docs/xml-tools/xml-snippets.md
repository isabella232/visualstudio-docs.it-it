---
title: frammenti XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c261893b50a217d888300ca01f3bc190bc065c94
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658766"
---
# <a name="xml-snippets"></a>frammenti XML

L'editor XML offre una funzionalità, denominata *frammenti XML*, che consente di creare file XML più rapidamente. È possibile riutilizzare i frammenti di codice XML inserendoli nei file. È inoltre possibile generare dati XML in base a uno schema di XML Schema Definition Language (XSD).

## <a name="reusable-xml-snippets"></a>Frammenti XML riutilizzabili

Nell'editor XML sono inclusi molti frammenti di codice che coprono alcune attività comuni. e che facilitano la creazione di file XML. Se ad esempio si sta creando una XML Schema, usando i frammenti di codice "elemento Sequence di tipo complesso" e "elemento di tipo semplice" si inserisce il testo XML seguente nel file. Il valore `name` può quindi essere modificato in base alle esigenze.

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

È possibile inserire i frammenti di codice in due modi diversi: Il comando **Insert Snippet** inserisce il frammento XML in corrispondenza della posizione del cursore. Il comando **Racchiudi tra** racchiude il frammento XML intorno al testo selezionato. Entrambi i comandi sono disponibili dal sottomenu **IntelliSense** nel menu **modifica** o dal menu di scelta rapida all'interno dell'editor.

Per altre informazioni, vedere [procedura: usare frammenti di codice XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Frammenti XML generati dallo schema

L'editor XML è inoltre in grado di generare un frammento XML da un XML Schema. Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento. Per altre informazioni, vedere [procedura: generare un frammento XML da un XML Schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Crea nuovi frammenti di codice XML

Oltre ai frammenti di codice inclusi in Visual Studio per impostazione predefinita, è anche possibile creare e utilizzare frammenti XML personalizzati. Per altre informazioni, vedere [procedura: creare frammenti XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Vedere anche

- [Frammenti di codice in Visual Studio](../ide/code-snippets.md)
- [Editor XML](../xml-tools/xml-editor.md)