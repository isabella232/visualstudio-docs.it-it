---
title: Esposizione di tipi alle finestre di progettazione visiva . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708430"
---
# <a name="expose-types-to-visual-designers"></a>Esporre i tipi alle finestre di progettazione visivaExpose types to visual designers
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Deve avere accesso alle definizioni di classe e tipo in fase di progettazione per visualizzare una finestra di progettazione visiva. Le classi vengono caricate da un set predefinito di assembly che includono il set di dipendenze completo del progetto corrente (riferimenti più le relative dipendenze). Potrebbe anche essere necessario per le finestre di progettazione visiva accedere a classi e tipi definiti nei file generati dagli strumenti personalizzati.

 I [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemi e di progetto forniscono il supporto per l'accesso a classi e tipi generati tramite file eseguibili portabili temporanei (PE temporanei). Qualsiasi file generato da uno strumento personalizzato può essere compilato in un assembly temporaneo in modo che i tipi possano essere caricati da tali assembly ed esposti alle finestre di progettazione. L'output di ogni strumento personalizzato viene compilato in un file PE temporaneo separato e l'esito positivo o negativo di questa compilazione temporanea dipende solo dalla possibilità o meno che il file generato possa essere compilato o meno. Anche se un progetto può non essere compilato nel suo complesso, i singoli PE temporanei potrebbero essere ancora disponibili per i progettisti.

 Il sistema del progetto fornisce il supporto completo per tenere traccia delle modifiche apportate al file di output di uno strumento personalizzato, a condizione che tali modifiche siano il risultato dell'esecuzione dello strumento personalizzato. Ogni volta che viene eseguito lo strumento personalizzato, viene generato un nuovo file PE temporaneo e vengono inviate le notifiche appropriate alle finestre di progettazione.

> [!NOTE]
> Poiché il file di generazione eseguibile del programma temporaneo si verifica in background, non vengono segnalati errori all'utente se la compilazione non riesce.

 Gli strumenti personalizzati che sfruttano il supporto PE temporaneo devono seguire le seguenti regole:

- **GeneratesDesignTimeSource** deve essere impostato su 1 nel Registro di sistema.

     Nessuna compilazione di file eseguibile di programma avviene senza questa impostazione.

- Il codice generato deve essere nella stessa lingua dell'impostazione globale del progetto.

     Il file PE temporaneo viene compilato indipendentemente da ciò che lo strumento personalizzato segnala come estensione richiesta a condizione <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> che **GeneratesDesignTimeSource** sia impostato su 1 nel Registro di sistema. Non è necessario che l'estensione sia *vb*, *cs*o *jsl*; può essere qualsiasi estensione.

- Il codice generato dallo strumento personalizzato deve essere valido e deve essere compilato da solo utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> solo il set di riferimenti presenti nel progetto al termine dell'esecuzione.

     Quando viene compilato un file PE temporaneo, l'unico file di origine fornito al compilatore è l'output dello strumento personalizzato. Pertanto, uno strumento personalizzato che utilizza un file PE temporaneo deve generare file di output che possono essere compilati indipendentemente da altri file nel progetto.

## <a name="see-also"></a>Vedere anche
- [Introduzione all'oggetto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementare generatori a file singolo](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrare generatori a file singolo](../../extensibility/internals/registering-single-file-generators.md)
