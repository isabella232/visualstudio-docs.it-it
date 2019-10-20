---
title: Frammenti di codice XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669354"
---
# <a name="xml-snippets"></a>Frammenti di codice XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor XML offre una funzionalità, denominata *frammenti XML*, che consente di creare file XML più rapidamente. È possibile riutilizzare i frammenti di codice XML inserendoli nei file. È possibile inoltre generare dati XML basati su uno schema XSD (XML Schema Definition Language).

## <a name="reusable-xml-snippets"></a>Frammenti di codice XML riutilizzabili
 L'editor XML include diversi frammenti di codice che comprendono alcune delle attività più comuni e che facilitano la creazione di file XML. Ad esempio, se si sta creando uno schema XML, usando i frammenti "Elemento Sequence di tipo complesso" e "Elemento di tipo semplice" sarà possibile inserire il seguente testo XML nel file. Il valore `name` può quindi essere modificato in base alle esigenze.

```
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

 È possibile inserire i frammenti di codice in due modi diversi: Il comando **Insert Snippet** inserisce il frammento XML in corrispondenza della posizione del cursore. Il comando **Racchiudi tra** racchiude il frammento XML intorno al testo selezionato. Entrambi i comandi sono disponibili dal sottomenu **IntelliSense** nel menu **modifica** o dal menu di scelta rapida dell'editor.

 Per altre informazioni, vedere [procedura: usare frammenti di codice XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Frammenti di codice XML generati da uno schema
 L'editor XML è in grado anche di generare un frammento di codice XML da uno schema XML. Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento.

 Per altre informazioni, vedere [procedura: generare un frammento XML da uno schema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Creazione di nuovi frammenti di codice XML
 Oltre ai frammenti di codice inclusi in [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio per impostazione predefinita, è anche possibile creare e utilizzare frammenti XML personalizzati.

 Per altre informazioni, vedere [procedura: creare frammenti XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Vedere anche
 [Editor XML](../xml-tools/xml-editor.md)
