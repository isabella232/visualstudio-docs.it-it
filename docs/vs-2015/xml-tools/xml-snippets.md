---
title: Frammenti di codice XML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf1ebeb70931e2e12f056ecfbaa45a6833e031df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183963"
---
# <a name="xml-snippets"></a>Frammenti di codice XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'Editor XML offre una funzionalità denominata *frammenti di codice XML*, che consente di compilare più rapidamente i file XML. È possibile riutilizzare i frammenti di codice XML inserendoli nei file. È possibile inoltre generare dati XML basati su uno schema XSD (XML Schema Definition Language).  
  
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
  
 È possibile inserire i frammenti di codice in due modi diversi: Il **Inserisci frammento di codice** comando inserisce il frammento XML in corrispondenza della posizione del cursore. Il **Racchiudi** comando esegue il wrapping di frammenti XML intorno al testo selezionato. Entrambi i comandi sono disponibili dal **IntelliSense** sottomenu di sotto il **modificare** dal menu o nel menu di scelta rapida dell'editor.  
  
 Per altre informazioni, vedere [procedura: usare frammenti di codice XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Frammenti di codice XML generati da uno schema  
 L'editor XML è in grado anche di generare un frammento di codice XML da uno schema XML. Tale funzionalità consente di inserire nell'elemento gli elementi XML generati dalle informazioni sullo schema per quel determinato elemento.  
  
 Per altre informazioni, vedere [procedura: generare un frammento di codice da un XML Schema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Creazione di nuovi frammenti di codice XML  
 Oltre ai frammenti inclusi in [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio per impostazione predefinita è anche possibile creare e usare frammenti XML personalizzati.  
  
 Per altre informazioni, vedere [procedura: creare frammenti di codice XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)



