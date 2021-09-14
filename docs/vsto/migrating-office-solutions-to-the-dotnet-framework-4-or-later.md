---
title: Eseguire Office soluzioni al .NET Framework 4 o versione successiva
description: Informazioni su come eseguire la migrazione Office soluzioni al .NET Framework 4 o versione successiva in modo che il progetto continui a funzionare.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 36ad3fa7fb59dcef142030d16dda5f637427a378
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710609"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Eseguire Office soluzioni al .NET Framework 4 o versione successiva
  Se il framework di destinazione di un progetto Office viene modificato in o versione successiva da una versione precedente del .NET Framework, potrebbero essere necessari alcuni passaggi aggiuntivi per continuare a eseguire la soluzione nei computer di sviluppo e degli utenti [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] finali. Per altre informazioni, vedere Modifiche necessarie per eseguire Office progetti di cui si esegue la migrazione al .NET Framework 4 o [.NET Framework 4.5.](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

 Inoltre, il progetto potrebbe non venire più compilato. Alcune funzionalità dei progetti di Office dispongono di modelli di programmazione diversi per le diverse versioni di .NET Framework. Quando il framework di destinazione di un progetto di Office viene modificato per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva da una versione precedente di .NET Framework, è necessario apportare le seguenti modifiche al codice del progetto:

- [Aggiornare Excel e i progetti word di cui si esegue la migrazione al .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aggiornare le personalizzazioni della barra multifunzione Office progetti di cui si esegue la migrazione al .NET Framework 4 o .NET Framework 4.5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aggiornare le aree del modulo Outlook progetti di cui si esegue la migrazione al .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Il framework di destinazione di un progetto di Office cambia quando si aggiorna il progetto da una versione precedente di Visual Studio. Per altre informazioni, vedere [Aggiornare ed eseguire la migrazione Office soluzioni](../vsto/upgrading-and-migrating-office-solutions.md).

  Per altre informazioni sul motivo per cui alcune funzionalità nei progetti Office hanno un modello di programmazione diverso quando si fa riferimento a o versioni successive, vedere Modifiche alla progettazione di progetti Office che hanno come destinazione .NET Framework 4 o la panoramica del runtime [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [di .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) e [Visual Studio Tools per Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Vedi anche
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Procedura: Scegliere una versione di .NET Framework di destinazione](../ide/visual-studio-multi-targeting-overview.md)
- [Risolvere gli errori nelle Office soluzioni](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Supporto aggiuntivo per gli errori nelle soluzioni Office aggiuntive](../vsto/additional-support-for-errors-in-office-solutions.md)
