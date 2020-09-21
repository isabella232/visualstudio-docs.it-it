---
title: Modifiche richieste per i progetti di Office migrate a .NET Framework 4, 4,5
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 773a4dd319d00487b919721bf3390a7d58c8b03c
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810967"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Modifiche necessarie per eseguire i progetti di Office di cui si esegue la migrazione al .NET Framework 4 o al .NET Framework 4,5
  Se il Framework di destinazione di un progetto di Office viene modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive da una versione precedente del .NET Framework, è necessario eseguire le attività seguenti per assicurarsi che la soluzione possa essere eseguita nel computer di sviluppo e nei computer degli utenti finali:

- Rimuovere l'oggetto <xref:System.Security.SecurityTransparentAttribute> dal progetto se è stato aggiornato da Visual Studio 2008.

- Eseguire un comando **Pulisci** in Visual Studio per poter eseguire o eseguire il debug del progetto nel computer di sviluppo.

- Aggiornare il prerequisito di .NET Framework per il progetto.

- Gli utenti finali devono anche reinstallare la soluzione se in precedenza è stata distribuita con ClickOnce prima dell'impostazione di un framework di destinazione diverso.

  Per altre informazioni su queste attività, vedere le sezioni corrispondenti riportate di seguito.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Rimuovere l'attributo SecurityTransparent dai progetti che si aggiornano da Visual Studio 2008
 Se si aggiorna un progetto di Office da Visual Studio 2008 e il framework di destinazione del progetto viene successivamente modificato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario rimuovere <xref:System.Security.SecurityTransparentAttribute> dal progetto. Visual Studio non rimuove automaticamente questo attributo. Se non si rimuove questo attributo, viene visualizzato un messaggio di errore quando si compila il progetto.

 Per ulteriori informazioni sulle condizioni in cui Visual Studio può modificare il Framework di destinazione di un progetto aggiornato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , vedere [aggiornamento e migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md).

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

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Eseguire il comando Pulisci per eseguire il debug o eseguire un progetto nel computer di sviluppo
 Se un progetto di Office è stato compilato prima della modifica del Framework di destinazione del progetto in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, è necessario eseguire un comando **Pulisci** e quindi ricompilare il progetto dopo la modifica del Framework di destinazione. Se non si esegue un comando **pulito** , si riceverà un oggetto <xref:System.Runtime.InteropServices.COMException> quando si tenta di eseguire il debug o di eseguire il progetto ridestinato.

 Per ulteriori informazioni sul comando **Pulisci** , vedere [compilazione di soluzioni Office](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Aggiornare i prerequisiti per la distribuzione
 Quando si ridestina un progetto di Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, è necessario aggiornare anche il prerequisito .NET Framework corrispondente nella finestra di dialogo **prerequisiti** . In caso contrario, i controlli di progetto limited di InstallShield la distribuzione ClickOnce o per e installa una versione precedente di .NET Framework.

 Per ulteriori informazioni sull'aggiornamento dei prerequisiti per la distribuzione ai computer degli utenti finali, vedere [procedura: installare i prerequisiti nei computer degli utenti finali per eseguire soluzioni Office](/previous-versions/bb608608(v=vs.110)).

## <a name="reinstall-solutions-on-end-user-computers"></a>Reinstallare le soluzioni nei computer degli utenti finali
 Se si usa ClickOnce per distribuire una soluzione Office destinata a .NET Framework 3.5 e quindi si modifica la destinazione del progetto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, gli utenti finali devono disinstallare la soluzione e reinstallarla dopo averla ripubblicata. Se si ripubblica la soluzione ridestinata e la soluzione viene aggiornata sui computer degli utenti finali, gli utenti finali riceveranno un <xref:System.Runtime.InteropServices.COMException> quando eseguiranno la soluzione aggiornata.

## <a name="see-also"></a>Vedere anche
- [Eseguire la migrazione di soluzioni Office a .NET Framework 4 o versione successiva](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)