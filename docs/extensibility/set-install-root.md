---
title: Installazione all'esterno della cartella delle estensioni con VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09b3b23a89450bb1abac4f8ebb10d00396a251b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433144"
---
# <a name="installing-outside-the-extensions-folder"></a>Installazione all'esterno della cartella delle estensioni

A partire da Visual Studio 2017 e VSIX v3 (versione 3), è ora supportata per l'installazione di asset di estensione esternamente alla cartella delle estensioni. Attualmente, i percorsi seguenti vengono abilitati come percorsi di installazione valido (dove [INSTALLDIR] viene eseguito il mapping alla directory di installazione dell'istanza di Visual Studio):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* \Licenses [INSTALLDIR]
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets

>**Nota:** Il formato VSIX non consente di installare di fuori della struttura di cartelle di installazione di Visual Studio.

Per supportare l'installazione in queste directory, l'estensione VSIX deve essere installato "per ogni istanza per ogni macchina". Questa opzione può essere abilitata selezionando la casella di controllo "tutti gli utenti" nella finestra di progettazione Extension. vsixmanifest:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Come impostare l'elemento InstallRoot

Per impostare le directory di installazione, è possibile usare la **proprietà** finestra in Visual Studio. Ad esempio, è possibile impostare il `InstallRoot` proprietà di un riferimento a una posizione precedente:

![proprietà radice di installazione](media/install-root-properties.png)

Verrà aggiunto alcuni metadati per il corrispondente `ProjectReference` proprietà all'interno di file con estensione csproj del progetto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Nota:** Se si preferisce, è possibile modificare direttamente il file con estensione csproj.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Come impostare un percorso secondario sotto l'elemento InstallRoot

Se si desidera installare in un percorso secondario sotto la `InstallRoot`, è possibile farlo impostando la `VsixSubPath` come proprietà di `InstallRoot` proprietà. Ad esempio, supponiamo si desidera visualizzare l'output del riferimento al nostro progetto per l'installazione di ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. È possibile farlo facilmente con la finestra di progettazione di proprietà:

![sottopercorso set](media/set-subpath.png)

Le modifiche di csproj corrispondente avrà un aspetto simile al seguente:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche di progettazione di proprietà si applicano solo ai riferimenti al progetto; è possibile impostare il `InstallRoot` metadati per gli elementi all'interno del progetto anche (usando gli stessi metodi descritti in precedenza).
