---
title: Installazione all'esterno della cartella extensions con VSIX v3 | Microsoft Docs
description: Informazioni sull'installazione Visual Studio asset dell'estensione SDK all'esterno della cartella extensions e sui percorsi validi.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f09b6d8a586a03aea8401a9125d6d1c43b77c845
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158255"
---
# <a name="install-outside-the-extensions-folder"></a>Eseguire l'installazione all'esterno della cartella delle estensioni

A partire Visual Studio 2017 e VSIX v3 (versione 3), gli asset di estensione possono essere installati all'esterno della cartella extensions. Attualmente, i percorsi seguenti sono abilitati come percorsi di installazione validi (dove [INSTALLDIR] è mappato alla directory di installazione dell'Visual Studio dell'istanza di :

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (supportato solo per Visual Studio 2017; deprecato per Visual Studio 2019 e versioni successive)

> [!NOTE]
> Il formato VSIX non consente di eseguire l'installazione all'esterno della Visual Studio di cartelle di installazione. 

Per supportare l'installazione in queste directory, vsix deve essere installato "per istanza per computer". Questa opzione può essere abilitata selezionando la casella di controllo "tutti gli utenti" nella finestra di progettazione extension.vsixmanifest:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Come impostare InstallRoot

Per impostare le directory di installazione, è possibile usare la **finestra Proprietà** in Visual Studio. Ad esempio, è possibile impostare la `InstallRoot` proprietà di un riferimento al progetto su una delle posizioni precedenti:

![installare le proprietà radice](media/install-root-properties.png)

Verranno aggiunti alcuni metadati alla proprietà corrispondente all'interno del file con estensione csproj del progetto `ProjectReference` VSIX:

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

Se si desidera eseguire l'installazione in un sottopercorso sotto , è possibile farlo impostando la proprietà come `InstallRoot` `VsixSubPath` la proprietà `InstallRoot` . Ad esempio, si vuole che l'output del riferimento al progetto sia installato in '[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. È possibile eseguire questa operazione facilmente con la finestra di progettazione delle proprietà:

![impostare il sottopercorso](media/set-subpath.png)

Le modifiche con estensione csproj corrispondenti saranno simili alle seguenti:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche apportate alla finestra di progettazione delle proprietà si applicano a più di un semplice riferimento al progetto. è possibile impostare anche i metadati per gli elementi all'interno del progetto `InstallRoot` (usando gli stessi metodi descritti in precedenza).
