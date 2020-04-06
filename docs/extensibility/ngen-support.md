---
title: Supporto di Ngen in VSIX v3 Documenti Microsoft
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702406"
---
# <a name="ngen-support-in-vsix-v3"></a>Supporto di Ngen in VSIX v3

Con Visual Studio 2017 e il nuovo formato di manifesto di estensione VSIX v3 (versione 3), gli sviluppatori di estensioni possono ora "ngen" i loro assembly in fase di installazione.

Di seguito è riportato un estratto da MSDN che spiega cosa fa "ngen":

>Il generatore di immagini native (*Ngen.exe*) è uno strumento che consente di migliorare le prestazioni delle applicazioni gestite. *Ngen.exe* crea immagini native, ovvero file contenenti codice computer specifico del processore compilato, e le installa nella cache delle immagini native nel computer locale. Il runtime può usare le immagini native della cache anziché il compilatore Just-In-Time (JIT) per compilare l'assembly originale.
>
>da [Ngen.exe (Generatore di immagini native)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Per "ngen" un assembly, il vSIX deve essere installato "per istanza per computer". Questo può essere abilitato selezionando la casella di `extension.vsixmanifest` controllo "tutti gli utenti" nella finestra di progettazione:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Come abilitare Ngen

Per abilitare ngen per un assembly, è possibile utilizzare la finestra Proprietà in Visual Studio.To enable ngen for an assembly, you can use the **Properties** window in Visual Studio.

Ci sono 4 proprietà che possono essere impostate:

1. **Ngen** (Boolean) - Se true, il programma di installazione di Visual Studio "ngen" l'assembly.
2. **Applicazione Ngen** (stringa): Ngen offre l'opportunità di usare il file *app.config* di un'applicazione per risolvere le dipendenze dell'assembly. Questo valore deve essere impostato su un'applicazione il cui *file app.config* si desidera utilizzare (relativo alla directory di installazione di Visual Studio).
3. **Architettura Ngen** (enum) - L'architettura per compilare in modo nativo l'assembly. Le opzioni sono: a. NotSpecified b. X86 c. X64 d. Tutti
4. **Priorità Ngen** (integer compresa tra 1 e 3) - Il livello di priorità Ngen è documentato nei livelli di [priorità Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Ecco uno sguardo alla finestra **Proprietà** in azione:

![ngen nelle proprietà](media/ngen-in-properties.png)

In questo modo verranno aggiunti metadati al riferimento al progetto all'interno del file *con estensione csproj* del progetto VSIX:

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

Le modifiche apportate alla finestra di progettazione delle proprietà si applicano a più riferimenti al progetto; è possibile impostare i metadati Ngen per gli elementi all'interno del progetto (utilizzando gli stessi metodi descritti in precedenza) purché gli elementi siano assembly .NET.
