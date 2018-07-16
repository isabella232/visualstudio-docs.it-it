---
title: Attività XmlPoke | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31c76ba53e858d9eab41d6579950f47b16f8c9b8
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37056355"
---
# <a name="xmlpoke-task"></a>Attività XmlPoke

Imposta i valori come specificato da una query XPath in un file XML.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `XmlPoke` .
  
|Parametro|Descrizione|
|---------------|-----------------|
|`Namespaces`|Parametro `String` facoltativo.<br /><br /> Specifica gli spazi dei nomi per i prefissi della query XPath. `Namespaces` è un frammento XML costituito da elementi `Namespace` con attributi `Prefix` e `Uri`. L'attributo `Prefix` specifica il prefisso da associare allo spazio dei nomi specificato nell'attributo `Uri`. Non usare un elemento `Prefix` vuoto.|
|`Query`|Parametro `String` facoltativo.<br /><br /> Specifica la query XPath.|
|`Value`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il valore da inserire nel percorso specificato.|
|`XmlInputPath`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica l'input XML come percorso di file.|

## <a name="remarks"></a>Note

 Oltre a usare i parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

Ecco un sample.xml da modificare:

```
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

In questo esempio, se si vuole modificare `/Package/mp:PhoneIdentity/PhonePublisherId` usare

```
<Project>
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` è qui usato come un prefisso artificiale dello spazio dei nomi per lo spazio dei nomi predefinito.

## <a name="see-also"></a>Vedere anche

 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
