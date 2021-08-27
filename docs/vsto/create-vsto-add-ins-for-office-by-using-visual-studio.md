---
title: Creare componenti aggiuntivi VSTO per Office con Visual Studio
description: Informazioni su come usare gli strumenti Microsoft Office per sviluppatori in Visual Studio per creare applicazioni .NET Framework che estendono Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 46330c69b89b297b82ce70d3fb6eb0b7bd7d95df
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/26/2021
ms.locfileid: "122981073"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Creare componenti aggiuntivi VSTO per Office con Visual Studio
> [!IMPORTANT]
> VSTO si basa [sull'.NET Framework](/dotnet/framework/get-started/overview). I componenti aggiuntivi COM possono anche essere scritti con il .NET Framework. Office Non è possibile creare componenti aggiuntivi con [.NET Core e .NET 5+](/dotnet/core/dotnet-five), le versioni più recenti di .NET. Ciò è dovuto al fatto che .NET Core/.NET 5+ non può funzionare con .NET Framework nello stesso processo e può causare errori di caricamento dei componenti aggiuntivi. È possibile continuare a usare .NET Framework per scrivere VSTO e componenti aggiuntivi COM per Office. Microsoft non aggiorerà VSTO piattaforma del componente aggiuntivo COM per usare .NET Core o .NET 5+. È possibile sfruttare .NET Core e .NET 5+, incluso ASP.NET Core, per creare il lato server di Office [componenti aggiuntivi Web.](/office/dev/add-ins/overview/office-add-ins)

  È possibile usare Microsoft Office Developer Tools in Visual Studio per creare applicazioni .NET Framework che estendono Office. Queste applicazioni sono denominate anche *soluzioni Office*.

 Office Developer Tools fornisce le funzionalità che consentono di creare soluzioni Office adatte alle diverse esigenze aziendali. Questi strumenti includono modelli di progetto che consentono di creare soluzioni Office con Visual Basic o Visual C# e finestre di progettazione visiva che permettono di creare interfacce utente personalizzate per le soluzioni Office.

[!include[Add-ins note](includes/addinsnote.md)]

 Per le informazioni più recenti sullo Office, vedere il Microsoft Office [developer center.](https://developer.microsoft.com/office/docs)

## <a name="in-this-section"></a>Contenuto della sezione
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)

 Fornisce collegamenti alle informazioni su come configurare un computer di sviluppo per creare soluzioni Office, su come iniziare a creare soluzioni Office e sulle novità relative allo sviluppo di Office in Visual Studio.

- [Aggiornare ed eseguire la migrazione Office soluzioni](upgrading-and-migrating-office-solutions.md)

 Fornisce collegamenti alle informazioni sul processo di aggiornamento per i progetti creati con versioni precedenti di Visual Studio.

- [Architettura delle Office soluzioni in Visual Studio](architecture-of-office-solutions-in-visual-studio.md)

 Fornisce collegamenti alle informazioni sul funzionamento delle soluzioni Office, incluse informazioni relative alle personalizzazioni a livello di documento e ai componenti aggiuntivi VSTO.

- [Progettare e creare Office soluzioni](designing-and-creating-office-solutions.md)

 Fornisce informazioni su come creare un progetto di Office e su come configurarlo in Visual Studio.

- [Sviluppare Office soluzioni](developing-office-solutions.md)

 Fornisce informazioni su come usare il codice gestito con le soluzioni Office, incluse informazioni su come personalizzare l'interfaccia utente di Office, gestire i dati e risolvere i problemi.

- [Excel soluzioni](excel-solutions.md)

 Fornisce informazioni su come automatizzare Excel, creare soluzioni Excel e affrontare i problemi di globalizzazione specifici di Excel.

- [Soluzioni InfoPath](infopath-solutions.md)

 Fornisce informazioni su come creare modelli di modulo e componenti aggiuntivi VSTO per InfoPath.

- [Outlook soluzioni](outlook-solutions.md)

 Fornisce informazioni su come automatizzare Outlook e creare componenti aggiuntivi VSTO e aree del modulo per Outlook.

- [PowerPoint soluzioni](powerpoint-solutions.md)

 Fornisce informazioni su come automatizzare PowerPoint e creare componenti aggiuntivi VSTO per PowerPoint.

- [Project soluzioni](project-solutions.md)

 Vengono fornite informazioni su come automatizzare Microsoft Office progetto e creare VSTO componenti aggiuntivi.

- [Visio soluzioni](visio-solutions.md)

 Fornisce informazioni su come automatizzare Visio e creare componenti aggiuntivi VSTO per Visio.

- [Soluzioni Word](word-solutions.md)

 Fornisce informazioni su come automatizzare Word e creare soluzioni Word.

- [Compilare Office soluzioni](building-office-solutions.md)

 Fornisce informazioni sulle differenze tra la creazione di progetti di Office e altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Eseguire il debug Office progetti](debugging-office-projects.md)

 Fornisce informazioni sulle differenze tra il debug di progetti di Office e altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Proteggere Office soluzioni](securing-office-solutions.md)

 Fornisce informazioni sull'uso delle funzionalità di sicurezza nelle soluzioni Office.

- [Distribuire una soluzione Office distribuzione](deploying-an-office-solution.md)

 Fornisce informazioni su come rendere disponibili agli utenti le soluzioni Office, nonché sui principali aspetti da considerare quando si sceglie un metodo di distribuzione.

- [Office esempi di sviluppo e procedure dettagliate](office-development-samples-and-walkthroughs.md)

 Fornisce collegamenti ad applicazioni di esempio e ad argomenti che illustrano le procedure dettagliate per l'esecuzione di attività comuni.

- [Informazioni di riferimento &#40;Office sviluppo in Visual Studio&#41;](general-reference-office-development-in-visual-studio.md)

 Fornisce collegamenti a informazioni dettagliate su Office assembly di interoperabilità primari, manifesti, elementi dell'interfaccia utente e messaggi di errore.

- [Riferimenti gestiti &#40;Office sviluppo in Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md)

 Fornisce collegamenti a informazioni sugli spazi dei nomi e i tipi di API usati nei progetti di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Per la documentazione di riferimento sulle API sugli spazi dei nomi e sui tipi usati nei progetti Office che hanno come destinazione .NET Framework 3.5, vedere la sezione di riferimento seguente nella documentazione di Visual Studio 2008: Riferimento gestito dal sistema [2007](managed-reference-office-development-in-visual-studio.md).

- [Informazioni di riferimento sulle API &#40;Office sviluppo in Visual Studio&#41;](unmanaged-api-reference-office-development-in-visual-studio.md)

 Contiene collegamenti a informazioni sulle interfacce COM che è possibile usare per eseguire azioni come caricare e scaricare componenti aggiuntivi VSTO gestiti nelle applicazioni di Office.

## <a name="related-sections"></a>Sezioni correlate
- [Office sviluppo con Visual Studio per sviluppatori](https://developer.microsoft.com/office/docs) Fornisce risorse aggiuntive, ad esempio articoli tecnici, video e blog.

- [Visual Studio developer center](https://visualstudio.microsoft.com/) Fornisce altre Visual Studio risorse, ad esempio articoli tecnici, video e blog.

- [Microsoft Office di sviluppo di MSDN Library](/previous-versions/office/office-12/bb726434(v=office.12)) Area di MSDN Library in cui è possibile trovare articoli e documentazione di riferimento sullo sviluppo di soluzioni per diverse versioni di Office (non specifiche dello sviluppo Office tramite Visual Studio).

- [Sviluppo di applicazioni in Visual Studio](/previous-versions/h8w79z10(v=vs.140)) Contiene collegamenti ad argomenti che illustrano come usare Visual Studio per progettare, sviluppare, eseguire il debug e distribuire applicazioni Web, servizi Web XML e applicazioni client tradizionali.

- [.NET Framework programmazione in Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Illustra lo sviluppo di applicazioni con .NET Framework in Visual Basic e Visual C#.
