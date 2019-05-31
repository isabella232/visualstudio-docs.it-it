---
title: 'Procedura dettagliata: Configurazione e utilizzo di un Set di regole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fa3a91df779094e3e11722dfc7bfc03c58bcea7e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383412"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Procedura dettagliata: Configurazione e uso di un set di regole personalizzate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come usare gli strumenti di analisi codice che sono stati configurati per usare un oggetto personalizzato *set di regole* in una libreria di classi. È possibile selezionare un set di regole che è correlato al tipo di progetto che è stato specificato per la soluzione, oppure è possibile selezionare set di regole alternativa per soddisfare esigenze specifiche, ad esempio l'analisi del codice legacy per i problemi che possono essere risolti in modo che non determina interruzione. In entrambi i casi, i set di regole possono essere personalizzati anche per adattarli ai propri requisiti di progetto.  
  
 In questa procedura dettagliata, avanzerà questi processi:  
  
- Creare una libreria di classi.  
  
- Selezionare il **regole base delle linee guida di progettazione Microsoft** set di regole di analisi del codice.  
  
- Aggiungere il proprio codice alla classe.  
  
- Esegui analisi del codice.  
  
- Personalizzare il set di regole.  
  
- Esegui analisi del codice e vedere come il set di regole comportamento delle personalizzazioni.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]o [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>Utilizza regole, viene impostato con l'analisi del codice  
 Innanzitutto, creare una libreria di classi semplici.  
  
#### <a name="create-a-class-library"></a>Creare una libreria di classi  
  
1. Scegliere **Nuovo** dal menu **File** , quindi fare clic su **Progetto**.  
  
2. Nel **nuovo progetto** nella finestra di dialogo **tipi di progetto**, fare clic su **Visual c#** .  
  
3. Sotto **Visual c#** , selezionare **libreria di classi**.  
  
4. Nel **Name** casella di testo, digitare **RuleSetSample** e quindi fare clic su **OK**.  
  
   Successivamente, si selezionerà il **regole base delle linee guida di progettazione Microsoft** set di regole e salvarlo con il progetto.  
  
#### <a name="select-a-code-analysis-rule-set"></a>Selezionare un set di regole di analisi codice  
  
1. Nel **Analyze** menu, fare clic su **Configura analisi codice per RuleSetSample**.  
  
    Vengono visualizzate le impostazioni di configurazione per l'analisi codice.  
  
2. Nel **eseguire questo set di regole** elenco a discesa, seleziona **tutte le regole Microsoft**.  
  
    Per altre informazioni sui set di regole disponibili, vedere [riferimento di set di regole di analisi di codice](../code-quality/code-analysis-rule-set-reference.md).  
  
    Nel menu File fare clic su **Salva elementi selezionati** per aggiornare il file di progetto con informazioni sui set di regole che è stata selezionata e le relative impostazioni.  
  
   > [!TIP]
   > In una situazione reale, una buona norma usare per definire la priorità dei problemi di destinazione con l'analisi del codice consiste nell'iniziare con il **regole minime** set di regole e correggere i problemi desiderati e quindi aggiungere in modo incrementale altre regole o regole imposta per trovare e correggere i problemi aggiuntivi.  
  
   Successivamente, si aggiungerà codice alla libreria di classi che verrà usata per dimostrare le violazioni del CA1704 "Gli identificatori devono essere digitati correttamente" regola di analisi del codice. Per altre informazioni, vedere [CA1704: Gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### <a name="add-your-own-code"></a>Aggiungere il proprio codice  
  
- In Esplora soluzioni aprire il file Class1.cs e sostituire il codice esistente con il codice seguente:  
  
  ```  
  using System;  
  using System.Collections.Generic;  
  using System.Text;  
  
  namespace RuleSetSample  
  {  
      public class Class1  
      {  
          //The variable parameter names "a" and "b" will cause  
          //the warning CA 1704 Microsoft.Naming "Consider   
          //providing a more meaningful name" to fire  
          public int AddIntegers(int a, int b)  
          {  
  
              int sum = a + b;  
  
              return (sum);  
          }  
      }  
  }  
  
  ```  
  
  A questo punto è possibile eseguire l'analisi del codice sul progetto RuleSetSample e cercare eventuali errori e avvisi generati nella finestra Elenco errori.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Esegui analisi del codice sul progetto RuleSetSample  
  
1. Nel **Analyze** menu, fare clic su **Esegui analisi del codice RuleSetSample**.  
  
2. Nella finestra Elenco errori, fare clic su **gli avvisi** e quindi fare clic sui **descrizione** intestazione di colonna per ordinare gli avvisi in modalità alfanumerica.  
  
    In un'applicazione reale, vorrebbero correggere eventuali violazioni delle regole vale la pena correzione a questo punto, o, facoltativamente, disattivare o eliminare una regola se è possibile determinare che non è stato necessario correggere. Per altre informazioni, vedere [Rimuovere avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3. Si noti che gli avvisi di CA1704. Tali violazioni di questa regola indicano che è "consigliabile fornire un nome più significativo per i parametri." È possibile correggere il problema nel codice oppure è possibile disabilitare la regola, come illustrato nella procedura successiva.  
  
   Successivamente si personalizzerà il set di regole per escludere l'avviso CA1704, "Gli identificatori devono essere digitati correttamente".  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizzare il set di regole per il progetto disabilitare una regola specifica  
  
1. Nel **Analyze** menu, fare clic su **Configura analisi codice per RuleSetSample**.  
  
2. Nel **eseguire questo set di regole** elenco a discesa elenco, verificare che il **tutte le regole Microsoft** regola set viene comunque evidenziato e quindi fare clic su **Open**. Verrà visualizzata la pagina di set di regole.  
  
3. Espandere il nodo della categoria Microsoft. naming e quindi selezionare l'avviso CA1704.  
  
4. Sotto il **azione** colonna, selezionare **None.** Ciò impedisce CA1704 venga visualizzato come un avviso o un errore nella finestra Elenco errori.  
  
    A questo punto sarebbe opportuno provare a usare i pulsanti della barra degli strumenti diversi e per acquisire familiarità con le opzioni di filtro. Ad esempio, è possibile usare la **Group By** elenco a discesa per consentire l'individuazione di una regola specifica, o categoria delle regole. Un altro esempio è che è possibile usare la **nascondere le regole disabilitate** pulsante sulla barra degli strumenti regola del set di pagine per nascondere o mostrare tutte le regole con il **azione** colonna impostata su **None**. Ciò può essere utile se si desidera cercare eventuali regole che è stata disattivata per verificare che si desidera abilitarle o meno.  
  
5. Dal menu Visualizza, fare clic sulla finestra Proprietà. Tipo di **My Custom Rule Set** nella casella nome della finestra degli strumenti delle proprietà. Questa operazione modificherà il nome visualizzato della nuova regola di cui il [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.  
  
6. Nel **File** menu, fare clic su **Rules.ruleset tutti i Microsoft salvare** per salvare la regola personalizzata impostata. Passare alla cartella radice del progetto. Nelle **il nome del file** casella di testo, digitare **SetRegolePersonalizzato**. È ora possibile selezionare il set di regole personalizzate per l'uso con il progetto.  
  
   Con il nuovo set di regole creato, a questo punto è necessario configurare le impostazioni del progetto per specificare che si desidera utilizzare il nuovo set di regole.  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Specificare la nuova regola impostata per l'uso con il progetto  
  
1. In Esplora soluzioni fare clic sul progetto e quindi selezionare **proprietà**.  
  
2. Nel **delle proprietà** scheda, fare clic su **analisi del codice**.  
  
    Nel **eseguire questo set di regole** elenco a discesa, fare clic su  **\<Sfoglia... >** . Passare alla cartella radice del progetto del codice e quindi selezionare **SetRegolePersonalizzato**. Questo è il nuovo set di regole creato nella procedura precedente.  
  
3. Nel **File** menu, fare clic su **salvare** per salvare la configurazione del progetto. Il set di regole personalizzate a questo punto è utilizzabile con il progetto.  
  
   Infine, verrà eseguito nuovamente usando il set di regole SetRegolePersonalizzato analisi del codice. Si noti che la finestra Elenco errori non vengono visualizzate alla violazione della regola delle prestazioni CA1704.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Esegui analisi codice sul progetto RuleSetSample per la seconda volta  
  
1. Nel **Analyze** menu, fare clic su **Esegui analisi del codice RuleSetSample**.  
  
2. Nella finestra Elenco errori, si noti che quando si fa clic **avvisi**, non si visualizzata più il segno di CA1704 per la regola "Gli identificatori devono essere digitati correttamente".  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Configura analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Tabella di riferimento del set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md)
