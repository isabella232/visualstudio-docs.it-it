---
title: Attività SignFile | Microsoft Docs
description: Informazioni su MSBuild'attività SignFile per firmare il file specificato usando il certificato specificato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d65187b74dc17c9211a6b3ac8b750606c1c4ae3d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625517"
---
# <a name="signfile-task"></a>SignFile (attività)

Consente di firmare il file specificato usando il certificato specificato.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `SignFile` .

 Notare che i certificati SHA-256 sono consentiti solo in computer con .NET 4.5 e versioni successive.

> [!WARNING]
> A partire da Visual Studio 2013 Update 3, questa attività ha una nuova firma che consente di specificare la versione del framework di destinazione per il file. L'utente è incoraggiato a usare la nuova firma, ove possibile, perché il processo di MSBuild usa gli hash SHA-256 solo quando il framework di destinazione è .NET 4.5 o versione successiva. Se il framework di destinazione è .NET 4.0 o versione precedente, l'hash SHA-256 non verrà usato.

|Parametro|Descrizione|
|---------------|-----------------|
|`CertificateThumbprint`|Parametro `String` obbligatorio.<br /><br /> Specifica il certificato da usare per la firma. Questo certificato deve trovarsi nell'archivio personale dell'utente corrente.|
|`SigningTarget`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica i file da firmare con il certificato, di tipo .exe o .dll.|
|`TimestampUrl`|Parametro `String` facoltativo.<br /><br /> Specifica l'URL del server di timestamp.|
|`TargetFrameworkVersion`|La versione di.NET Framework che viene usata per la destinazione.|

## <a name="remarks"></a>Commenti

 Oltre ai parametri sopra elencati, quest'attività eredita i parametri dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base attività](../msbuild/task-base-class.md).

## <a name="example"></a>Esempio

 Nell'esempio seguente viene usata l'attività `SignFile` per firmare i file specificati nella raccolta di elementi `FilesToSign` con il certificato specificato dalla proprietà `CertificateThumbprint`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> L'identificazione personale del certificato è l'hash SHA-1 del certificato. Per altre informazioni, vedere [Ottenere l'hash SHA-1 di un certificato CA radice attendibile](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Se si copia e incolla l'identificazione personale presente nei dettagli del certificato, assicurarsi di non includere il carattere invisibile (3F) aggiuntivo, che può impedire a `SignFile` di trovare il certificato.

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Attività](../msbuild/msbuild-tasks.md)