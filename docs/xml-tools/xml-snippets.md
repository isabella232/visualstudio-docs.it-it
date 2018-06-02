---
title: Frammenti di codice XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07ddb1dd64e5d972c23a032cb1eb752515d92ab6
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693851"
---
# <a name="xml-snippets"></a>frammenti XML

L'Editor XML offre una funzionalità denominata *frammenti XML*, che consente di compilare più rapidamente i file XML. È possibile riutilizzare i frammenti di codice XML inserendoli nei file. È possibile inoltre generare dati XML basati su uno schema XSD (XML Schema Definition Language).

## <a name="reusable-xml-snippets"></a>Frammenti di codice XML riutilizzabili

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

 È possibile inserire i frammenti di codice in due modi diversi: Il **Inserisci frammento di codice** comando consente di inserire il frammento XML nella posizione del cursore. Il **Racchiudi** comando esegue il wrapping il frammento XML nel testo selezionato. Entrambi i comandi sono disponibili dal **IntelliSense** sottomenu di sotto di **modifica** dal menu o dal menu di scelta rapida dell'editor.

 Per altre informazioni, vedere [procedura: utilizzare XML snippets](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Frammenti XML generati dallo schema
 L'editor XML è in grado anche di generare un frammento di codice XML da uno schema XML. Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento.

 Per altre informazioni, vedere [procedura: generare un frammento XML da uno schema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Creare nuovi frammenti XML
 Oltre ai frammenti inclusi in [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio per impostazione predefinita, è anche possibile creare e usare i frammenti XML personalizzati.

 Per altre informazioni, vedere [procedura: creare XML snippets](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)