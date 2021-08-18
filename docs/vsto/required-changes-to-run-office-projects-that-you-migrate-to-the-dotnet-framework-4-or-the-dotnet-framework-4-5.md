---
title: Modifiche necessarie per i Office di cui è stata eseguita la migrazione a .NET 4.5
description: Informazioni sulle modifiche da apportare al progetto se il framework di destinazione viene modificato in .NET Framework 4 o versione successiva da una versione precedente del .NET Framework.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 8b1e3ca556e07e0d4df8a27142a0700fd40e09a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032225"
---
# <a name="changes-required-for-office-projects-migrated-to-net-45"></a>Modifiche necessarie per i Office di cui è stata eseguita la migrazione a .NET 4.5

  Se il framework di destinazione di un progetto Office viene modificato in o versione successiva da una versione precedente del .NET Framework, è necessario eseguire le attività seguenti per assicurarsi che la soluzione possa essere eseguita nel computer di sviluppo e nei computer degli utenti [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] finali:

- Rimuovere l'oggetto <xref:System.Security.SecurityTransparentAttribute> dal progetto se è stato aggiornato da Visual Studio 2008.

- Eseguire un **comando Clean** in Visual Studio essere in grado di eseguire o eseguire il debug del progetto nel computer di sviluppo.

- Aggiornare il prerequisito di .NET Framework per il progetto.

- Gli utenti finali devono anche reinstallare la soluzione se in precedenza è stata distribuita con ClickOnce prima dell'impostazione di un framework di destinazione diverso.

  Per altre informazioni su queste attività, vedere le sezioni corrispondenti riportate di seguito.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Rimuovere l'attributo SecurityTransparent dai progetti aggiornati da Visual Studio 2008
 Se si aggiorna un progetto di Office da Visual Studio 2008 e il framework di destinazione del progetto viene successivamente modificato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario rimuovere <xref:System.Security.SecurityTransparentAttribute> dal progetto. Visual Studio non rimuove automaticamente questo attributo. Se non si rimuove questo attributo, viene visualizzato un messaggio di errore quando si compila il progetto.

 Per altre informazioni sulle condizioni in cui Visual Studio modificare il framework di destinazione di un progetto aggiornato a o , vedere Aggiornare ed eseguire la migrazione Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [soluzioni](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>Per rimuovere SecurityTransparentAttribute

1. Con il progetto aperto in Visual Studio, aprire **Esplora soluzioni**.

2. Nel nodo **Proprietà** (per C#) o **Progetto personale** (per Visual Basic) fare doppio clic sul file di codice AssemblyInfo per aprirlo nell'editor di codice.

    > [!NOTE]
    > Per visualizzare il file di codice AssemblyInfo nei progetti di Visual Basic, è necessario fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni** .

3. Individuare <xref:System.Security.SecurityTransparentAttribute> e rimuoverlo dal file o impostarlo come commento.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Eseguire il comando clean per eseguire il debug o l'esecuzione di un progetto nel computer di sviluppo
 Se un progetto Office è stato compilato prima che il framework di destinazione del progetto venga modificato in o versione successiva, è necessario eseguire un comando Clean e quindi ricompilare il progetto dopo la modifica del [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] framework di destinazione.  Se non si esegue un **comando Clean,** si riceverà un quando si tenta di eseguire il debug o <xref:System.Runtime.InteropServices.COMException> di eseguire il progetto ridestinato.

 Per altre informazioni sul **comando Clean,** vedere [Build Office solutions](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Aggiornare i prerequisiti per la distribuzione
 Quando si ridestina un progetto Office a o versioni successive, è necessario aggiornare anche il prerequisito di .NET Framework corrispondente nella [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] **finestra di dialogo** Prerequisiti . In caso contrario, i controlli di progetto limited di InstallShield la distribuzione ClickOnce o per e installa una versione precedente di .NET Framework.

 Per altre informazioni sull'aggiornamento dei prerequisiti per la distribuzione nei computer degli utenti finali, vedere [Procedura:](/previous-versions/bb608608(v=vs.110))Installare i prerequisiti nei computer degli utenti finali per eseguire Office soluzioni .

## <a name="reinstall-solutions-on-end-user-computers"></a>Reinstallare le soluzioni nei computer degli utenti finali
 Se si usa ClickOnce per distribuire una soluzione Office destinata a .NET Framework 3.5 e quindi si modifica la destinazione del progetto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, gli utenti finali devono disinstallare la soluzione e reinstallarla dopo averla ripubblicata. Se si ripubblica la soluzione ridestinata e la soluzione viene aggiornata nei computer degli utenti finali, gli utenti finali riceveranno un messaggio quando eseguono <xref:System.Runtime.InteropServices.COMException> la soluzione aggiornata.

## <a name="see-also"></a>Vedi anche
- [Eseguire Office soluzioni di migrazione a .NET Framework 4 o versione successiva](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)