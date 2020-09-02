---
title: 'Procedura dettagliata: configurazione e uso di un set di regole personalizzate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645749"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Procedura dettagliata: Configurazione e uso di un set di regole personalizzate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come utilizzare gli strumenti di analisi del codice configurati per l'utilizzo di un *set di regole* personalizzato in una libreria di classi. È possibile selezionare un set di regole che si riferisce al tipo di progetto specificato per la soluzione oppure è possibile selezionare set di regole alternativi per soddisfare una specifica esigenza, ad esempio l'analisi del codice legacy per individuare i problemi che possono essere corretti in modo non interrompente. In entrambi i casi, è inoltre possibile personalizzare i set di regole per ottimizzarli ai requisiti del progetto.

 In questa procedura dettagliata si eseguiranno i passaggi seguenti:

- Creare una libreria di classi.

- Selezionare il set di regole di analisi del codice per le **linee guida di Microsoft Basic Design** .

- Aggiungere codice personalizzato alla classe.

- Eseguire l'analisi del codice.

- Personalizzare il set di regole.

- Eseguire l'analisi del codice e verificare il funzionamento del comportamento di personalizzazione del set di regole.

## <a name="prerequisites"></a>Prerequisiti

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]o [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Uso di set di regole con l'analisi del codice
 Per prima cosa, creare una libreria di classi semplice.

#### <a name="create-a-class-library"></a>Creare una libreria di classi

1. Nel menu **File** fare clic su **Nuovo** e quindi su **Progetto**.

2. Nella finestra di dialogo **nuovo progetto** , in **Tipi progetto**, fare clic su **Visual C#**.

3. In **Visual C#** selezionare **libreria di classi**.

4. Nella casella di testo **nome** digitare **RuleSetSample** e quindi fare clic su **OK**.

   A questo punto, selezionare il set di **regole Microsoft Basic Design Guideline** Rules e salvarlo con il progetto.

#### <a name="select-a-code-analysis-rule-set"></a>Selezionare un set di regole di analisi del codice

1. Nel menu **analizza** fare clic su **Configura analisi codice per RuleSetSample**.

    Verranno visualizzate le impostazioni di configurazione per l'analisi del codice.

2. Nell'elenco a discesa **Esegui questo set di regole** selezionare **Microsoft all Rules**.

    Per ulteriori informazioni sui set di regole disponibili, vedere [riferimento al set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md).

    Scegliere **Salva elementi selezionati** dal menu file per aggiornare il file di progetto con le informazioni sul set di regole selezionato e le relative impostazioni.

   > [!TIP]
   > In una situazione reale, una procedura consigliata per la definizione delle priorità dei problemi che si desidera utilizzare per l'analisi del codice consiste nell'iniziare con il set di regole **minime consigliate** e correggere i problemi desiderati, quindi aggiungere in modo incrementale altre regole o set di regole per individuare e correggere i problemi aggiuntivi.

   Successivamente, si aggiungerà codice alla libreria di classi che verrà usato per illustrare le violazioni della regola di analisi del codice di CA1704 "identificatori". Per altre informazioni, vedere [CA1704: gli identificatori devono essere digitati correttamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Aggiungere codice personalizzato

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

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Eseguire l'analisi del codice nel progetto RuleSetSample

1. Nel menu **analizza** fare clic su **Esegui analisi del codice in RuleSetSample**.

2. Nella finestra Elenco errori fare clic su **avvisi** e quindi sull'intestazione di colonna **Descrizione** per ordinare gli avvisi in modo alfanumerico.

    In un'applicazione reale, è necessario correggere le eventuali violazioni delle regole che è opportuno correggere a questo punto o facoltativamente disattivare o eliminare una regola se è stato determinato che la correzione non è stata corretta. Per altre informazioni, vedere [Rimuovere avvisi tramite l'attributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Si notino gli avvisi CA1704. Queste violazioni in questa regola indicano che è necessario fornire un nome più significativo per i parametri. È possibile risolvere il problema nel codice oppure disabilitare la regola, come illustrato nella procedura seguente.

   Successivamente, verrà personalizzato il set di regole in modo da escludere l'avviso di CA1704, "gli identificatori devono essere digitati correttamente".

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizzare il set di regole per il progetto in modo da disabilitare una regola specifica

1. Nel menu **analizza** fare clic su **Configura analisi codice per RuleSetSample**.

2. Nell'elenco a discesa **Esegui questo set** di regole verificare che il set di regole **Microsoft all Rules** sia ancora evidenziato, quindi fare clic su **Apri**. Verrà visualizzata la pagina set di regole.

3. Espandere il nodo Microsoft. naming Category, quindi selezionare l'avviso CA1704.

4. Nella colonna **azione** selezionare **nessuno.** Ciò impedisce la visualizzazione di CA1704 come un avviso o un errore nella finestra Elenco errori.

    A questo punto è opportuno provare i diversi pulsanti della barra degli strumenti e le opzioni di filtro per acquisire familiarità con essi. Ad esempio, è possibile usare l'elenco a discesa **raggruppa** per per individuare una regola specifica o una categoria di regole. Un altro esempio è che è possibile usare il pulsante **Nascondi regole disabilitate** nella barra degli strumenti pagine set di regole per nascondere o mostrare tutte le regole con la colonna **azione** impostata su **None**. Questa operazione può essere utile se si desidera eseguire l'analisi di tutte le regole disattivate per verificare che siano ancora disabilitate.

5. Scegliere Finestra Proprietà dal menu Visualizza. Digitare **My Custom Rule Set** nella casella nome della finestra degli strumenti Proprietà. Verrà modificato il nome visualizzato del nuovo set di regole nell' [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.

6. Scegliere **Salva Microsoft all Rules. RuleSet** dal menu **file** per salvare il set di regole personalizzato. Passare alla cartella radice del progetto. Nella casella di testo **nome file** digitare **MyCustomRuleSet**. Il set di regole personalizzate ora può essere selezionato per l'uso con il progetto.

   Con il nuovo set di regole creato, è ora necessario configurare le impostazioni del progetto per specificare che si vuole usare il nuovo set di regole.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Specificare il nuovo set di regole da usare con il progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.

2. Nella scheda **Proprietà** fare clic su **analisi codice**.

    Nell'elenco a discesa **Esegui questo set di regole** fare clic su **\<Browse..>** . Passare alla cartella radice del progetto di codice e quindi selezionare **MyCustomRuleSet. RuleSet**. Si tratta del nuovo set di regole creato nella procedura precedente.

3. Nel menu **file** fare clic su **Salva** per salvare la configurazione del progetto. Il set di regole personalizzate ora può essere usato con il progetto.

   Infine, sarà necessario eseguire di nuovo l'analisi del codice usando il set di regole MyCustomRuleSet. Si noti che nella finestra Elenco errori non viene visualizzata la violazione della regola delle prestazioni CA1704.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Esegui analisi del codice sul progetto RuleSetSample per la seconda volta

1. Nel menu **analizza** fare clic su **Esegui analisi del codice in RuleSetSample**.

2. Nella finestra Elenco errori si noti che quando si fa clic su **avvisi**, non vengono più visualizzate le violazioni di avviso CA1704 per la regola "identificatori che devono essere digitati correttamente".

## <a name="see-also"></a>Vedere anche
 [Procedura: configurare l'analisi del codice per un riferimento al set di regole di analisi del codice di un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [Code analysis rule set reference](../code-quality/code-analysis-rule-set-reference.md)
