---
title: frammenti XML
description: Informazioni sulla funzionalità dei frammenti XML nell'editor XML che consente di compilare i file XML più rapidamente riutilizzando i frammenti XML e inserendoli nei file.
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
ms.openlocfilehash: b48ee5ad1d7dcd2782ada6df0a6db66af58a92ee63946f904ae37540ba6f674b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121295982"
---
# <a name="xml-snippets"></a>frammenti XML

L'editor XML offre una funzionalità, denominata *frammenti XML,* che consente di compilare i file XML più rapidamente. È possibile riutilizzare i frammenti di codice XML inserendoli nei file. È inoltre possibile generare dati XML in base a uno schema XSD (XML Schema Definition Language).

## <a name="reusable-xml-snippets"></a>Frammenti XML riutilizzabili

L'editor XML include molti frammenti di codice che coprono alcune attività comuni. e che facilitano la creazione di file XML. Ad esempio, se si crea uno schema XML, l'uso dei frammenti di codice "Elemento sequenza di tipi complessi" e "Elemento di tipo semplice" inserisce il testo XML seguente nel file. Il valore `name` può quindi essere modificato in base alle esigenze.

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

È possibile inserire i frammenti di codice in due modi diversi: Il **comando Inserisci frammento** inserisce il frammento XML in corrispondenza della posizione del cursore. Il **comando Racchiude tra** racchiude il frammento XML intorno al testo selezionato. Entrambi i comandi sono disponibili dal sottomenu **IntelliSense** nel **menu** Modifica o dal menu di scelta rapida nell'editor.

Per altre informazioni, vedere [Procedura: Usare frammenti XML.](../xml-tools/how-to-use-xml-snippets.md)

## <a name="schema-generated-xml-snippets"></a>Frammenti XML generati da schema

L'editor XML è inoltre in grado di generare un frammento XML da uno schema XML. Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento. Per altre informazioni, vedere [Procedura: Generare un frammento XML da uno schema XML.](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)

## <a name="create-new-xml-snippets"></a>Creare nuovi frammenti XML

Oltre ai frammenti di codice inclusi in Visual Studio per impostazione predefinita, è anche possibile creare e usare frammenti XML personalizzati. Per altre informazioni, vedere [Procedura: Creare frammenti XML.](../xml-tools/how-to-create-xml-snippets.md)

## <a name="see-also"></a>Vedi anche

- [Frammenti di codice in Visual Studio](../ide/code-snippets.md)
- [Editor XML](../xml-tools/xml-editor.md)
