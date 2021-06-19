---
title: 'Procedura: Eseguire la migrazione di un progetto Domain-Specific linguistico'
description: Fornisce informazioni su come eseguire la migrazione di un progetto di linguaggio specifico di dominio a una versione più recente di Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 8119f465e32d3754dc446524286e0a2c12dedc40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387190"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Procedura: eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione
È possibile eseguire la migrazione di progetti che definiscono e usano un linguaggio specifico di dominio a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] dalla versione di distribuita con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Uno strumento di migrazione viene fornito come parte di [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . Lo strumento converte Visual Studio progetti e soluzioni che usano o definiscono strumenti DSL.

 È necessario eseguire lo strumento di migrazione in modo esplicito: non viene avviato automaticamente quando si apre una soluzione in Visual Studio. Lo strumento e il documento di istruzioni dettagliate sono disponibili in questo percorso:

 **%Programmi%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Prima di eseguire la migrazione dei progetti DSL
 Lo strumento di migrazione modifica Visual Studio file di progetto (**con estensione csproj**) e file di soluzione (**sln**).

#### <a name="to-prepare-projects-for-migration"></a>Per preparare i progetti per la migrazione.

- Assicurarsi che **i file con estensione csproj** e **sln** possano essere scritti. Se sono sotto controllo del codice sorgente, assicurarsi che siano estratti.

- Creare una copia delle cartelle di cui si intende eseguire la migrazione.

## <a name="migrating-a-collection-of-projects"></a>Migrazione di una raccolta di progetti

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Per eseguire la migrazione di progetti e soluzioni DSL Visual Studio 2010

1. Avviare l'Utilità di migrazione DSL.

   - È possibile fare doppio clic su di Esplora risorse (o Esplora file) o avviare lo strumento da un prompt dei comandi. Lo strumento si trova in questa posizione:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Scegliere una cartella contenente soluzioni e progetti da convertire.

   - Immettere il percorso nella casella nella parte superiore dello strumento oppure fare clic su **Sfoglia**.

     Lo strumento di migrazione visualizza un albero di progetti che definiscono o usano le DSL. L'albero include ogni progetto che usa gli assembly **Microsoft.VisualStudio.Modeling.Sdk** o **TextTemplating.**

3. Esaminare l'albero dei progetti e deselezionare i progetti che non si desidera convertire.

   - Selezionare un progetto o una soluzione per visualizzare un elenco di modifiche che verranno apportate con lo strumento.

       > [!NOTE]
       > Le caselle di controllo visualizzate accanto ai nomi delle cartelle non hanno alcun effetto. È necessario espandere le cartelle per esaminare i progetti e le soluzioni.

4. Convertire i progetti.

   1. Fare clic **su Converti**.

        Prima della conversione di ogni file di progetto, una copia del progetto con estensione **csproj** viene salvata come progetto con estensione **vs2008.csproj**

        Una copia di ogni _soluzione_**con estensione sln** viene salvata _come soluzione_**.vs2008.sln**

   2. Esaminare eventuali conversioni non riuscite segnalate.

        Gli errori vengono segnalati nella finestra di testo. Inoltre, la visualizzazione albero mostra un flag rosso in ogni nodo che non è riuscito a eseguire la conversione. È possibile fare clic sul nodo per ottenere altre informazioni sull'errore.

5. **Trasformare tutti i modelli** in soluzioni contenenti progetti convertiti correttamente.

   1. Aprire la soluzione.

   2. Fare clic **sul pulsante Trasforma tutti i** modelli nell'intestazione Esplora soluzioni.

       > [!NOTE]
       > È possibile rendere questo passaggio superfluo. Per altre informazioni, vedere [Come automatizzare la trasformazione di tutti i modelli.](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))

6. Aggiornare il codice personalizzato nei progetti convertiti.

   - Provare a compilare i progetti ed esaminare eventuali errori.

   - Testare la finestra di progettazione.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedi anche

- [Post di blog correlati](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)