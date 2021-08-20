---
title: Supporto di Ngen in VSIX v3 | Microsoft Docs
description: Informazioni su come abilitare il generatore di immagini native, uno strumento che gli sviluppatori di estensioni possono usare per migliorare le prestazioni delle applicazioni gestite.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0ca58451057c1cea15e0e99ff221595d525c1732
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094568"
---
# <a name="ngen-support-in-vsix-v3"></a>Supporto di Ngen in VSIX v3

Con Visual Studio 2017 e il nuovo formato del manifesto dell'estensione VSIX v3 (versione 3), gli sviluppatori di estensioni possono ora "ngen" i propri assembly in fase di installazione.

Di seguito è riportato un estratto di MSDN che spiega cosa fa "ngen":

>Il generatore di immagini native (*Ngen.exe*) è uno strumento che migliora le prestazioni delle applicazioni gestite. *Ngen.exe* crea immagini native, ovvero file contenenti codice macchina specifico del processore compilato, e le installa nella cache delle immagini native nel computer locale. Il runtime può usare le immagini native della cache anziché il compilatore Just-In-Time (JIT) per compilare l'assembly originale.
>
>from [Ngen.exe (generatore di immagini native)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Per "ngen" un assembly, vsix deve essere installato "per istanza per computer". Questa opzione può essere abilitata selezionando la casella di controllo "tutti gli utenti" nella finestra di `extension.vsixmanifest` progettazione:

![controlla tutti gli utenti](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Come abilitare Ngen

Per abilitare ngen per un assembly, è possibile usare la **finestra** Proprietà in Visual Studio.

È possibile impostare 4 proprietà:

1. **Ngen** (booleano): se true, il Visual Studio di installazione "ngen" l'assembly.
2. **Applicazione Ngen** (stringa): Ngen offre la possibilità di usare il *file* app.configdi un'applicazione per risolvere le dipendenze dell'assembly. Questo valore deve essere impostato su un'applicazione *di cuiapp.config* che si vuole usare (rispetto alla directory Visual Studio di installazione).
3. **Architettura Ngen** (enumerazione): architettura per compilare in modo nativo l'assembly. Le opzioni sono: a. NotSpecified b. X86 c. X64 d. Tutti
4. **Priorità Ngen** (numero intero compreso tra 1 e 3): il livello di priorità Ngen è documentato [Ngen.exe priorità.](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)

Ecco un'occhiata alla **finestra Proprietà** in azione:

![ngen nelle proprietà](media/ngen-in-properties.png)

Verranno aggiunti metadati al riferimento al progetto all'interno del file con estensione *csproj del progetto* VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Se si preferisce, è possibile modificare direttamente il file con estensione csproj.

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche apportate alla finestra di progettazione delle proprietà non si applicano solo ai riferimenti al progetto. È possibile impostare anche i metadati Ngen per gli elementi all'interno del progetto (usando gli stessi metodi descritti in precedenza) purché gli elementi siano assembly .NET.
