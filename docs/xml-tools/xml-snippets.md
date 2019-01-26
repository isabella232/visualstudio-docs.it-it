---
title: Frammenti di codice XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 649617ac905e7d81ea68c5e5550dc106fbe1c24d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020958"
---
# <a name="xml-snippets"></a>frammenti XML

L'Editor XML offre una funzionalità denominata *frammenti di codice XML*, che consente di compilare più rapidamente i file XML. È possibile riutilizzare i frammenti di codice XML inserendoli nei file. È possibile inoltre generare dati XML basati su uno schema XSD (XML Schema Definition Language).

## <a name="reusable-xml-snippets"></a>Frammenti XML riutilizzabili

L'editor XML include diversi frammenti di codice che comprendono alcune delle attività più comuni e che facilitano la creazione di file XML. Ad esempio, se si sta creando uno schema XML, usando i frammenti "Elemento Sequence di tipo complesso" e "Elemento di tipo semplice" sarà possibile inserire il seguente testo XML nel file. Il valore `name` può quindi essere modificato in base alle esigenze.

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

 È possibile inserire i frammenti di codice in due modi diversi: Il **Inserisci frammento di codice** comando inserisce il frammento XML in corrispondenza della posizione del cursore. Il **Racchiudi** comando esegue il wrapping di frammenti XML intorno al testo selezionato. Entrambi i comandi sono disponibili dal **IntelliSense** sottomenu di sotto il **modificare** dal menu o nel menu di scelta rapida dell'editor.

 Per altre informazioni, vedere [Procedura: Usare frammenti di codice XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Frammenti XML generati da uno schema
 L'editor XML è in grado anche di generare un frammento di codice XML da uno schema XML. Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento.

 Per altre informazioni, vedere [Procedura: Generare un frammento XML da uno schema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Creare nuovi frammenti XML
 Oltre ai frammenti inclusi in [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio per impostazione predefinita è anche possibile creare e usare frammenti XML personalizzati.

 Per altre informazioni, vedere [Procedura: Creare frammenti XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)