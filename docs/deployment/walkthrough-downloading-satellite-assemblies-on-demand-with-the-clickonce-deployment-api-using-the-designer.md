---
title: Scaricare l'assembly satellite su richiesta usando ClickOnce progettazione
description: Informazioni su come contrassegnare gli assembly satellite come facoltativi usando Progettazione e scaricare solo l'assembly necessario a un computer client per le impostazioni cultura correnti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 42973e84237de5095676809e3f861b2726f44f87
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133588"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Procedura dettagliata: Scaricare gli assembly satellite su richiesta con l'API ClickOnce distribuzione tramite la finestra di progettazione
Le applicazioni Windows Form possono essere configurate per più impostazioni cultura con l'uso di assembly satellite. Un *assembly satellite* è un assembly in cui sono contenute risorse dell'applicazione per impostazioni cultura diverse da quelle predefinite dell'applicazione.

 Come illustrato in [Localizzazione ClickOnce applicazioni](../deployment/localizing-clickonce-applications.md), è possibile includere più assembly satellite per più impostazioni cultura all'interno della stessa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scaricherà tutti gli assembly satellite nella distribuzione nel computer client, anche se probabilmente un singolo client richiederà un solo assembly satellite.

 Questa procedura dettagliata descrive come contrassegnare gli assembly satellite come facoltativi e scaricare solo l'assembly di cui un computer client ha bisogno per le impostazioni cultura correnti.

> [!NOTE]
> Ai fini dell'esecuzione del test, nei seguenti esempi di codice viene specificato `ja-JP` a livello di codice per le impostazioni cultura. Per informazioni su come modificare il codice per un ambiente di produzione, vedere la sezione "Passaggi successivi" più avanti in questo argomento.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Per contrassegnare gli assembly satellite come facoltativi

1. Compilare il progetto. In questo modo verranno generati gli assembly satellite per tutte le impostazioni cultura in cui si sta eseguendo la localizzazione.

2. Fare clic con il pulsante destro del mouse sul nome del progetto in Esplora soluzioni, quindi scegliere **Proprietà**.

3. Fare clic sulla scheda **Pubblica**, quindi su **File applicazione**.

4. Selezionare la casella di controllo **Mostra tutti i file** per visualizzare gli assembly satellite. Per impostazione predefinita, tutti gli assembly satellite verranno inclusi nella distribuzione e saranno visibili in questa finestra di dialogo.

     Un assembly satellite avrà un nome nel formato\ApplicationName.resources.dll *\<isoCode> ,* dove è un identificatore di lingua \<isoCode> in formato RFC 1766.

5. Scegliere **Nuovo** nell'elenco **Gruppo di download** per ogni identificatore del linguaggio. Quando viene richiesto di specificare un nome per il gruppo di download, immettere l'identificatore del linguaggio. Ad esempio, per un assembly satellite giapponese, è necessario specificare il nome del gruppo di download `ja-JP` .

6. Chiudere la finestra di dialogo **File applicazione**.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Per scaricare assembly satellite su richiesta in C\#

1. Aprire il file *Program.cs.* Se questo file non è visualizzato in Esplora soluzioni, selezionare il progetto e scegliere **Mostra tutti i file** dal menu **Progetto**.

2. Usare il codice seguente per scaricare l'assembly satellite appropriato e avviare l'applicazione.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs" id="Snippet1":::

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Per scaricare assembly satellite su richiesta in Visual Basic

1. Fare clic sulla scheda **Applicazione** nella finestra **Proprietà** dell'applicazione.

2. Nella parte inferiore della pagina della scheda, scegliere **Visualizza eventi di applicazioni**.

3. Nella parte iniziale del file *ApplicationEvents.VB*, aggiungere i seguenti riferimenti importati.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet1":::

4. Aggiungere il codice seguente alla classe `MyApplication` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb" id="Snippet2":::

## <a name="next-steps"></a>Passaggi successivi
 In un ambiente di produzione sarà probabilmente necessario rimuovere la riga degli esempi di codice usata per impostare la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> su un valore specifico, perché il valore predefinito per i computer client è quello corretto. Quando l'applicazione è in esecuzione su un computer client giapponese, ad esempio, la proprietà predefinita <xref:System.Threading.Thread.CurrentUICulture%2A> sarà `ja-JP` . L'impostazione di tale proprietà a livello di codice è un buon metodo per procedere alla verifica degli assembly satellite prima di distribuire l'applicazione.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Scaricare assembly satellite su richiesta con l'API ClickOnce distribuzione](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Localizzazione delle applicazioni ClickOnce](../deployment/localizing-clickonce-applications.md)
