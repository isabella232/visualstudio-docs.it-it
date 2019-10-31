---
title: Eseguire la migrazione di soluzioni Office a .NET Framework 4 o versione successiva
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9531f0495bd0dc0a9f095ff71fdfd84fc8d1380
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189774"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Eseguire la migrazione di soluzioni Office a .NET Framework 4 o versione successiva
  Se il Framework di destinazione di un progetto di Office viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva da una versione precedente del .NET Framework, potrebbero essere necessari alcuni passaggi aggiuntivi per continuare a eseguire la soluzione nei computer di sviluppo e degli utenti finali. Per ulteriori informazioni, vedere [la pagina relativa alle modifiche necessarie per eseguire i progetti di Office di cui si esegue la migrazione al .NET Framework 4 o al .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Inoltre, il progetto potrebbe non venire più compilato. Alcune funzionalità dei progetti di Office dispongono di modelli di programmazione diversi per le diverse versioni di .NET Framework. Quando il framework di destinazione di un progetto di Office viene modificato per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva da una versione precedente di .NET Framework, è necessario apportare le seguenti modifiche al codice del progetto:

- [Aggiornare i progetti di Excel e Word di cui si esegue la migrazione al .NET Framework 4 o al .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aggiornare le personalizzazioni della barra multifunzione nei progetti di Office di cui si esegue la migrazione al .NET Framework 4 o al .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aggiornare le aree del modulo nei progetti Outlook di cui si esegue la migrazione al .NET Framework 4 o al .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Il framework di destinazione di un progetto di Office cambia quando si aggiorna il progetto da una versione precedente di Visual Studio. Per altre informazioni, vedere eseguire l' [aggiornamento e la migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Per altre informazioni sui motivi per cui alcune funzionalità nei progetti di Office hanno un modello di programmazione diverso quando si ha come destinazione la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versione successiva, vedere [modifiche alla progettazione dei progetti di Office destinati a .NET Framework 4 o .NET Framework 4,5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) e [Visual Panoramica di Studio Tools per Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Vedere anche
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Procedura: destinare una versione di .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Risolvere gli errori nelle soluzioni Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Supporto aggiuntivo per gli errori nelle soluzioni Office](../vsto/additional-support-for-errors-in-office-solutions.md)
