---
title: Installazione all'esterno della cartella Extensions con VSIX V3 | Microsoft Docs
description: Informazioni sull'installazione di asset di estensioni di Visual Studio SDK all'esterno della cartella Extensions e sui percorsi validi.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73bfb963122762c3185a964826a11dca5e771717
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716016"
---
# <a name="install-outside-the-extensions-folder"></a>Eseguire l'installazione all'esterno della cartella delle estensioni

A partire da Visual Studio 2017 e VSIX V3 (versione 3), gli asset di estensione possono essere installati all'esterno della cartella estensioni. Attualmente, i percorsi seguenti sono abilitati come percorsi di installazione validi (dove [INSTALLDIR] è mappato alla directory di installazione dell'istanza di Visual Studio):

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\schemas.
* [INSTALLDIR] \Common7\ide\publicassemblies.
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (supportata solo per Visual Studio 2017; deprecato per Visual Studio 2019 e versioni successive)

> [!NOTE]
> Il formato VSIX non consente di installare all'esterno della struttura di cartelle di installazione di Visual Studio. 

Per supportare l'installazione in queste directory, è necessario installare il progetto VSIX "per istanza per computer". Questa operazione può essere abilitata selezionando la casella di controllo "tutti gli utenti" nella finestra di progettazione dell'estensione vsixmanifest:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Come impostare InstallRoot

Per impostare le directory di installazione, è possibile usare la finestra **Proprietà** in Visual Studio. È ad esempio possibile impostare la `InstallRoot` proprietà di un riferimento a un progetto su uno dei percorsi indicati in precedenza:

![installa proprietà radice](media/install-root-properties.png)

I metadati vengono aggiunti alla `ProjectReference` proprietà corrispondente all'interno del file con estensione csproj del progetto VSIX:

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

Se si vuole eseguire l'installazione in un sottopercorso sotto `InstallRoot` , è possibile impostare la `VsixSubPath` proprietà come la `InstallRoot` Proprietà. Si immagini, ad esempio, che l'output del riferimento al progetto venga installato in ' [INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0'. Questa operazione può essere eseguita facilmente con la finestra di progettazione delle proprietà:

![imposta sottopercorso](media/set-subpath.png)

Le modifiche. csproj corrispondenti appariranno come segue:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche di progettazione proprietà si applicano solo a riferimenti a progetti. è anche possibile impostare i `InstallRoot` metadati per gli elementi all'interno del progetto (usando gli stessi metodi descritti in precedenza).
