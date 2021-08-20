---
title: '&lt;Elemento fileAssociation &gt; (ClickOnce Application) | Microsoft Docs'
description: L'elemento fileAssociation identifica un'estensione di file da associare all'applicazione. L'elemento fileAssociation è facoltativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: a17f239b7abaf981416b86ec785cb7a4d7e95e8a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160816"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;Elemento fileAssociation &gt; (applicazione ClickOnce)
Identifica un'estensione di file da associare all'applicazione.

## <a name="syntax"></a>Sintassi

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `fileAssociation` è facoltativo. L'elemento presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`extension`|Obbligatorio. Estensione di file da associare all'applicazione.|
|`description`|Obbligatorio. Descrizione del tipo di file che può essere utilizzato dalla shell.|
|`progid`|Obbligatorio. Nome che identifica in modo univoco il tipo di file.|
|`defaultIcon`|Obbligatorio. Specifica l'icona da usare per i file con questa estensione. Il file dell'icona deve essere specificato usando [ \<file> l'elemento all'interno](../deployment/file-element-clickonce-application.md) [ \<assembly> dell'elemento](../deployment/assembly-element-clickonce-application.md) che contiene questo elemento.|

## <a name="remarks"></a>Commenti
 Questo elemento deve includere un riferimento allo spazio dei nomi XML "urn:schemas-microsoft-com:clickonce.v1". Se `<fileAssociation>` l'elemento viene usato, deve essere successivo `<application>` all'elemento nel relativo elemento [ \<assembly> padre.](../deployment/assembly-element-clickonce-application.md)

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non sovrascriverà le associazioni di file esistenti. Tuttavia, un'ClickOnce può eseguire l'override dell'estensione di file solo per l'utente corrente. Dopo che ClickOnce'applicazione viene disinstallata, ClickOnce elimina l'associazione di file per l'utente e l'associazione per computer è di nuovo attiva.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente vengono illustrati `fileAssociation` gli elementi in un manifesto dell'applicazione per un'applicazione dell'editor di testo distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Questo esempio di codice include anche [ \<file> l'elemento](../deployment/file-element-clickonce-application.md) richiesto `defaultIcon` dall'attributo .

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)