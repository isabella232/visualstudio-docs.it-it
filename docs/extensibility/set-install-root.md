---
title: Installazione all'esterno della cartella delle estensioni con VSIX v3 Documenti Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700174"
---
# <a name="install-outside-the-extensions-folder"></a>Eseguire l'installazione all'esterno della cartella delle estensioni

A partire da Visual Studio 2017 e VSIX v3 (versione 3), gli asset di estensione possono essere installati all'esterno della cartella delle estensioni. Attualmente, i percorsi seguenti sono abilitati come percorsi di installazione validi (dove [INSTALLDIR] è mappato alla directory di installazione dell'istanza di Visual Studio):

* [INSTALLDIR]-MSBuild (informazioni in base alla soddisfazione dei genitori)
* [INSTALLDIR], Xml, Schemi
* [INSTALLDIR]-Common7/IDE/PublicAssemblies
* [INSTALLDIR]-Licenze
* [INSTALLDIR]-Common7/IDE/ReferenceAssemblies
* [INSTALLDIR]-Common7/IDE/RemoteDebugger
* [INSTALLDIR] , Common7 , IDE , VC , VCTargets (supportato solo per Visual Studio 2017; deprecato per Visual Studio 2019 e versioni successive)

> [!NOTE]
> Il formato VSIX non consente di installare all'esterno della struttura di cartelle di installazione di Visual Studio.The VSIX format doesn't allow you to install outside the Visual Studio install folder structure. 

Per supportare l'installazione in queste directory, il progetto VSIX deve essere installato "per istanza per computer". Questo può essere abilitato selezionando la casella di controllo "tutti gli utenti" nella finestra di progettazione extension.vsixmanifest:This can be enabled by checking the "all-users" checkbox in the extension.vsixmanifest designer:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Come impostare il InstallRoot

Per impostare le directory di installazione, è possibile utilizzare la finestra Proprietà in Visual Studio.To set the installation directories, you can use the **Properties** window in Visual Studio. Ad esempio, è `InstallRoot` possibile impostare la proprietà di un riferimento di progetto su uno dei percorsi sopra indicati:

![installare le proprietà radice](media/install-root-properties.png)

In questo modo alcuni `ProjectReference` metadati alla proprietà corrispondente all'interno del file con estensione csproj del progetto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Se si preferisce, è possibile modificare direttamente il file con estensione csproj.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Come impostare un sottopercorso nella finestra InstallRoot

Se si desidera eseguire l'installazione in `InstallRoot`un sottopercorso sotto `VsixSubPath` il , `InstallRoot` è possibile impostare la proprietà proprio come la proprietà. Si supponga, ad esempio, di voler eseguire l'output del riferimento al progetto in '[INSTALLDIR]'MSBuild'MyCompany'MySDK'1.0'. Possiamo farlo facilmente con il progettista di proprietà:

![impostare il sottopercorso](media/set-subpath.png)

Le modifiche con estensione csproj corrispondente avranno il seguente aspetto:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche apportate alla finestra di progettazione delle proprietà si applicano a più riferimenti al progetto; è possibile `InstallRoot` impostare i metadati anche per gli elementi all'interno del progetto (utilizzando gli stessi metodi descritti in precedenza).
