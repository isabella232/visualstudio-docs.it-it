---
title: Installazione all'esterno della cartella extensions con VSIX v3 | Microsoft Docs
description: Informazioni sull'installazione Visual Studio asset dell'estensione SDK all'esterno della cartella delle estensioni e sui percorsi validi.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24b1e1a73ff588e5531eec2025c8a3c9e94760a4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898448"
---
# <a name="install-outside-the-extensions-folder"></a>Eseguire l'installazione all'esterno della cartella delle estensioni

A partire Visual Studio 2017 e VSIX v3 (versione 3), gli asset di estensione possono essere installati all'esterno della cartella extensions. Attualmente, i percorsi seguenti sono abilitati come percorsi di installazione validi (dove [INSTALLDIR] è mappato alla directory Visual Studio di installazione dell'istanza di :

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (supportato solo per Visual Studio 2017; deprecato per Visual Studio 2019 e versioni successive)

> [!NOTE]
> Il formato VSIX non consente di eseguire l'installazione all'esterno della Visual Studio di cartelle di installazione. 

Per supportare l'installazione in queste directory, VSIX deve essere installato "per istanza per computer". Questa opzione può essere abilitata selezionando la casella di controllo "all-users" nella finestra di progettazione extension.vsixmanifest:

![controlla tutti gli utenti](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Come impostare InstallRoot

Per impostare le directory di installazione, è possibile usare la **finestra** Proprietà in Visual Studio. Ad esempio, è possibile impostare la `InstallRoot` proprietà di un riferimento al progetto su uno dei percorsi precedenti:

![installare le proprietà radice](media/install-root-properties.png)

Verranno aggiunti alcuni metadati alla proprietà corrispondente all'interno del file con estensione csproj del `ProjectReference` progetto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Se si preferisce, è possibile modificare direttamente il file con estensione csproj.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Come impostare un sottopercorso in InstallRoot

Se si desidera eseguire l'installazione in un sottopercorso sotto , è possibile farlo impostando la proprietà esattamente `InstallRoot` `VsixSubPath` come la proprietà `InstallRoot` . Ad esempio, si vuole che l'output del riferimento al progetto sia installato in '[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. È possibile eseguire facilmente questa operazione con la finestra di progettazione delle proprietà:

![impostare il sottopercorso](media/set-subpath.png)

Le modifiche csproj corrispondenti saranno simili alle seguenti:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche apportate alla finestra di progettazione delle proprietà non si applicano solo ai riferimenti al progetto. È possibile impostare anche i metadati per gli elementi all'interno del `InstallRoot` progetto (usando gli stessi metodi descritti in precedenza).
