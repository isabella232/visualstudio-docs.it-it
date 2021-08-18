---
title: '&lt;Elemento &gt; Strings (bootstrapper) | Microsoft Docs'
description: L'elemento Strings definisce stringhe localizzate per i nomi dei prodotti, i nomi dei pacchetti e i messaggi di errore di installazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c962435431164f78e542d9186bfe44c4659a3923
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073708"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Elemento &gt; Strings (programma di avvio automatico)
Definisce le stringhe localizzate per i nomi dei prodotti, i nomi dei pacchetti e i messaggi di errore di installazione.

## <a name="syntax"></a>Sintassi

```xml
<Strings>
    <String
        Name
    >
    </String>
</Strings>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 `Strings`L'elemento è un elemento figlio dell'elemento `Package` . Non ha attributi.

## <a name="string"></a>string
 `String`L'elemento è un elemento figlio dell'elemento `Strings` . Un `Strings` elemento può avere uno o più `String` elementi.

 `String` ha l'attributo seguente.

|Attributo|Descrizione|
|---------------|-----------------|
|`Name`|Obbligatorio. Nome della stringa.|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente vengono specificate tutte le stringhe in lingua inglese per il .NET Framework programma di installazione.

```xml
<Strings>
    <String Name="DisplayName">.NET Framework 2.0</String>
    <String Name="Culture">en</String>
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>
</Strings>
```

## <a name="see-also"></a>Vedi anche
- [\<Package> Elemento](../deployment/package-element-bootstrapper.md)