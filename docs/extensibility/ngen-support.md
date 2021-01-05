---
title: Supporto di NGen in VSIX V3 | Microsoft Docs
description: Informazioni su come abilitare Native Image Generator, uno strumento che gli sviluppatori di estensioni possono usare per migliorare le prestazioni delle applicazioni gestite.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 064176a0a28e3621e796bf60ede552f9cda155b0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864038"
---
# <a name="ngen-support-in-vsix-v3"></a>Supporto di Ngen in VSIX v3

Con Visual Studio 2017 e il nuovo formato manifesto di estensione VSIX V3 (versione 3), gli sviluppatori di estensioni possono ora "NGen" i rispettivi assembly al momento dell'installazione.

Di seguito è riportato un Estratto di MSDN che spiega cosa fa "NGen":

>Il generatore di immagini native (*Ngen.exe*) è uno strumento che migliora le prestazioni delle applicazioni gestite. *Ngen.exe* crea immagini native, ovvero file contenenti codice macchina compilato specifico del processore, e le installa nella cache delle immagini native nel computer locale. Il runtime può usare le immagini native della cache anziché il compilatore Just-In-Time (JIT) per compilare l'assembly originale.
>
>da [Ngen.exe (Generatore di immagini native)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Per "NGen" un assembly, VSIX deve essere installato "per istanza per computer". Questa operazione può essere abilitata selezionando la casella di controllo "tutti gli utenti" nella `extension.vsixmanifest` finestra di progettazione:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Come abilitare Ngen

Per abilitare NGen per un assembly, è possibile usare la finestra **Proprietà** in Visual Studio.

Sono disponibili 4 proprietà che è possibile impostare:

1. **NGen** (booleano): se è true, il programma di installazione di Visual Studio "NGen" l'assembly.
2. **Applicazione NGen** (stringa): NGen consente di usare un file di *app.config* dell'applicazione per risolvere le dipendenze degli assembly. Questo valore deve essere impostato su un'applicazione di cui si desidera utilizzare *app.config* (rispetto alla directory di installazione di Visual Studio).
3. **Architettura NGen** (enum): l'architettura per compilare in modo nativo l'assembly. Le opzioni sono: a. NotSpecified b. X86 c. X64 d. Tutti
4. **Priorità NGen** (numero intero compreso tra 1 e 3): il livello di priorità di NGen è documentato a [Ngen.exe livelli di priorità](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Di seguito è riportato un aspetto della finestra **Proprietà** in azione:

![Ngen nelle proprietà](media/ngen-in-properties.png)

In questo modo, i metadati vengono aggiunti al riferimento del progetto all'interno del file con *estensione csproj* del progetto VSIX:

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

Le modifiche di progettazione proprietà si applicano solo a riferimenti a progetti. è possibile impostare anche i metadati NGen per gli elementi all'interno del progetto (usando gli stessi metodi descritti in precedenza), purché gli elementi siano assembly .NET.
