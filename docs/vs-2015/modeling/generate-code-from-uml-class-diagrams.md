---
title: Generare codice dai diagrammi classi UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: e13ad8f658fafa2a20556e95123c5cd5965934e6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222834"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generare codice da diagrammi classi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per generare codice Visual c# .NET da diagrammi classi UML in Visual Studio, usare il **genera codice** comando. Per impostazione predefinita, il comando genera un tipo C# per ogni tipo UML selezionato. Tale comportamento può essere modificato o esteso modificando o copiando i modelli di testo che generano il codice. È possibile specificare un comportamento differente per i tipi contenuti nei vari pacchetti del modello.  
  
 Il **genera codice** comando è particolarmente indicato per la generazione di codice dalla selezione dell'utente di elementi e per la generazione di un file per ogni classe UML o un altro elemento. Ad esempio, nella schermata seguente sono illustrati due file C# generati da due classi UML.  
  
 In alternativa, se si desidera generare il codice in cui i file generati non è una relazione 1:1 con gli elementi UML, è possibile scrivere modelli di testo che vengono richiamati con il **Trasforma tutti i modelli** comando. Per altre informazioni su tale metodo, vedere [generare file da un modello UML](../modeling/generate-files-from-a-uml-model.md).  
  
 ![Diagramma ed C generato della classe UML&#35; file di classe. ](../modeling/media/oob-gencode1.png "oob_GenCode1")  
  
 Per altre informazioni sui diagrammi classi UML in Visual Studio, vedere gli argomenti seguenti:  
  
-   [Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)  
  
-   [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)  
  
 Per le versioni di Visual Studio che supportano i diagrammi classi UML, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="using-the-generate-code-command"></a>Utilizzo del comando Genera codice  
 La procedura seguente descrive il comportamento predefinito del **genera codice** comando:  
  
#### <a name="to-generate-a-separate-file-for-each-element"></a>Per generare un file separato per ogni elemento  
  
1.  Creare un modello UML contenente classi. È possibile applicare stereotipi agli elementi del modello.  
  
     Per altre informazioni, vedere [trasformazioni della generazione di codice predefinito](#default).  
  
2.  In un diagramma classi o nella **Esplora modelli UML**, selezionare gli elementi da cui si vuole generare il codice. È possibile effettuare una delle seguenti selezioni:  
  
    -   Un set specifico di elementi.  
  
    -   Un pacchetto o il modello, dal cui contenuto generare il codice.  
  
    -   Il diagramma, per selezionarne tutti gli elementi.  
  
3.  Aprire il menu di scelta rapida per un elemento selezionato e quindi scegliere **genera codice**.  
  
     La prima volta che usa **genera codice** in un particolare modello, viene visualizzata una finestra di dialogo. che consente di modificare i parametri di generazione del codice del modello.  
  
     Scegli **OK** a meno che non si sa che si desidera modificare questi parametri.  
  
     Per tornare alla finestra di dialogo in un secondo momento, aprire **Esplora modelli UML**. Apri menu di scelta rapida del progetto di modellazione e quindi scegliere **Configura generazione codice**. Per altre informazioni, vedere [personalizzazione del comando genera codice](#custom).  
  
 Vengono generati i file contenenti il codice C#. Nel caso predefinito, viene generato per ogni tipo un file in un progetto Libreria di classi C#. È tuttavia possibile personalizzare tale comportamento. Per altre informazioni, vedere [personalizzazione del comando genera codice](#custom).  
  
 Al modello vengono applicati alcuni test di convalida per verificare che possa essere convertito in C#. Se i test hanno esito negativo, viene visualizzato un messaggio di errore e la generazione di codice non viene eseguita. Se si è creato un comando di menu di convalida, il codice non viene generato per gli elementi per i quali il comando di convalida ha esito negativo. Per altre informazioni, vedere [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
##  <a name="default"></a> Trasformazioni della generazione di codice predefinita  
 In questa sezione riepiloga i risultati prodotti dal **genera codice** non è stato personalizzato il comando. Per altre informazioni, vedere [personalizzazione del comando genera codice](#custom).  
  
-   Per ogni tipo selezionato nel modello UML viene generato un tipo C#. Ogni tipo viene inserito in un file di codice separato nella **GeneratedCode** cartella.  
  
-   Se il tipo UML è contenuto in un pacchetto, il tipo C# generato viene inserito in uno spazio dei nomi e il file viene generato in una cartella con lo stesso nome dello spazio dei nomi.  
  
-   Per ogni elemento `Attribute` di una classe UML viene generata una proprietà C#.  
  
-   Per ogni elemento `Operation` di un tipo UML viene generato un metodo C#.  
  
-   Per ogni associazione navigabile cui partecipa la classe viene generato un campo C#.  
  
 Aggiungendo uno stereotipo a ogni tipo UML, è possibile controllare più proprietà del tipo C# generato.  
  
|**Per creare questo tipo c#**|**Creare il tipo UML**|**Applicare lo stereotipo**|  
|---------------------------------|----------------------------|-------------------------------|  
|Classe|Classe|\<None > oppure<br /><br /> Classe C#|  
|Interfaccia|Interfaccia|\<None > oppure<br /><br /> Interfaccia C#|  
|Enumerazione|Enumerazione|\<None > oppure<br /><br /> C# enum|  
|Delegato|Classe|Delegato C#|  
|Struct|Classe|C# struct|  
  
#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Per impostare uno stereotipo su un tipo o su un altro elemento  
  
1.  Aprire il menu di scelta rapida per l'elemento in un diagramma o in **Esplora modelli UML**, quindi scegliere **proprietà**.  
  
2.  Nel **delle proprietà** finestra, scegliere la freccia a discesa nel **stereotipi** proprietà e quindi selezionare la casella di controllo relativa allo stereotipo da applicare.  
  
    > [!TIP]
    >  Se gli stereotipi C# non sono visualizzati, abilitare il profilo C# per il modello o per un pacchetto contenente gli elementi del modello desiderati. Selezionare il pacchetto o la radice del modello nel **Esplora modelli UML**. Quindi nel **delle proprietà** finestra, scegliere **profilo**e quindi abilitare il profilo c#.  
  
3.  Espandere la **stereotipi** proprietà per visualizzare le proprietà aggiuntive che è possibile impostare.  
  
 Il **Description** le proprietà dei tipi, attributi, operazioni e le associazioni sono scritte `<summary>` commenti nel codice generato. Gli elementi di commento collegati ai tipi sono scritti in commenti `<remarks>`.  
  
## <a name="varying-the-generated-code"></a>Modifica del codice generato  
 Il codice generato varia in base alle proprietà di ciascun tipo, attributo o operazione. Ad esempio, se si imposta la **Is Abstract** proprietà di una classe su true, il `abstract` (parola chiave) verranno visualizzati nella classe generata. Se si impostano i **molteplicità** di un attributo su **0..\*** , quindi la proprietà generata disporrà di un `IEnumerable<>` tipo.  
  
 Inoltre, ogni stereotipo fornisce varie proprietà aggiuntive che è possibile impostare. Questi valori vengono convertiti nelle parole chiave appropriate nel codice C#. Ad esempio, se si imposta la proprietà `Is Static` su una classe, la classe C# sarà `static`.  
  
 Per impostare queste proprietà aggiuntive, selezionare la classe o un altro elemento nel diagramma. Nella finestra Proprietà, espandere **stereotipi**, quindi espandere lo stereotipo c#, ad esempio **classe c#**.  Per le classi, tali proprietà aggiuntive includono:  
  
-   CLR Attributes  
  
-   Is Partial  
  
-   Is Static  
  
-   Is Unsafe  
  
-   Package Visibility  
  
 Ogni attributo e operazione dispone di proprietà di stereotipo che è possibile impostare. Se non è possibile visualizzare le proprietà in un nuovo attributo, eseguire **genera codice**.  
  
##  <a name="custom"></a> Personalizzazione del comando genera codice  
 Il **genera codice** comando funziona mediante la trasformazione degli elementi del modello usando un set di modelli di testo. Per altre informazioni sui modelli di testo, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).  
  
 I modelli vengono specificati in un set di *associazioni modelli di testo*. Consente di specificare un'associazione di modelli di testo deve essere applicato il modello, in cui deve essere inserito l'output generato e altri parametri del **genera codice** comando.  
  
 Quando si esegue innanzitutto le **genera codice** comando su un particolare modello, collega un set predefinito di associazioni a modello alla radice del modello. Queste associazioni si applicano a tutti gli elementi del modello.  
  
 Tuttavia, è possibile eseguire l'override e aggiungere, a questi binding predefiniti, binding personalizzati a pacchetti, classi o altri elementi. Un binding si applica a tutti gli elementi contenuti nell'elemento a cui è collegata. Ad esempio, se si desidera che tutti i tipi contenuti in un particolare pacchetto vengano trasformati in base a un differente set di modelli o che vengano estratti in una diversa cartella, è possibile collegare le associazioni a modello al pacchetto.  
  
 Per controllare le associazioni del modello collegate a un elemento del modello, scegliere i puntini di sospensione **[...]**  nella **associazioni modelli di testo** proprietà nella finestra Proprietà.  
  
 Il **genera codice** comando applica i modelli a ciascun elemento del modello selezionato. Per ogni elemento, il set di modelli applicato è il set combinato dei modelli associati ai relativi contenitori, fino alla radice del modello inclusa.  
  
 Se due associazioni a modello in questo set hanno lo stesso nome, l'associazione nel contenitore più piccolo esegue l'override dell'associazione nel contenitore più grande. Ad esempio, la radice del modello ha un'associazione con il nome **modello di classe**. Per consentire a un modello personalizzato applicato al contenuto di un pacchetto specifico, definire il proprio associazione di modelli con il nome **modello di classe**.  
  
 È possibile applicare più modelli a un elemento del modello, nonché generare più file da ciascun elemento del modello.  
  
> [!NOTE]
>  Le associazioni collegate alla radice del modello fungono da associazioni predefinite per tutti gli elementi del modello. Per visualizzare questi binding predefiniti, aprire **Esplora modelli UML**. Aprire il menu di scelta rapida del progetto di modellazione, quindi scegliere **Configura generazione codice**. In alternativa è possibile selezionare la radice del modello in Esplora modelli UML. Nella finestra Proprietà scegliere **[...]**  nella **associazioni modelli di testo** proprietà. Le associazioni non verranno visualizzati fino a quando non è stata usata la **genera codice** comando almeno una volta. Non è possibile collegare binding a modello a un diagramma.  
  
#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Per collegare associazioni a modello di testo a un pacchetto o a un altro elemento del modello  
  
1.  Nelle **Esplora modelli UML**, aprire il menu di scelta rapida per un elemento del modello e quindi scegliere **proprietà**. In genere, le associazioni a modello di testo vengono collegate a un pacchetto o alla radice del modello.  
  
2.  Nel **delle proprietà** finestra, fare clic sul pulsante con puntini di sospensione (**[...]** ) nei **associazioni modelli di testo** proprietà.  
  
     Il **associazioni modelli di testo** verrà visualizzata la finestra di dialogo.  
  
3.  Scegli **Add** per creare una nuova associazione di modelli di testo.  
  
     \- oppure -  
  
     Scegliere un'associazione esistente per modificarla.  
  
     Ogni binding a modello definisce la modalità di applicazione di un modello specificato all'elemento del modello selezionato e agli altri elementi in questo contenuti.  
  
4.  Nella finestra di dialogo, impostare le proprietà del binding a modello di testo.  
  
    |**Property**|**Descrizione**|  
    |------------------|---------------------|  
    |nome|Nome per il binding. Per eseguire l'override di un binding ereditato da un pacchetto o da un modello che lo contiene, usare lo stesso nome del binding di cui si desidera eseguire l'override.|  
    |Overwrite|Se true, il codice esistente viene sovrascritto.|  
    |Target Name|Nome del file generato.<br /><br /> È possibile inserire le espressioni in questa stringa, ad esempio `{Name}` o `{Owner.Name}`. Ad esempio, è possibile scrivere: `{Owner.Name}_{Name}`. L'espressione viene valutata sull'elemento del modello e può usare proprietà di elementi, ma non metodi. Per trovare le proprietà possono essere usate, esaminare le proprietà dei tipi nella **Microsoft.VisualStudio.Uml.\*** . **Importante:** `{Name}` oppure `{Owner.Name}` può essere utilizzato solo nel **nome destinazione** proprietà. Per modificare il nome della classe generata, è necessario modificare il modello. Per altre informazioni, vedere [scrittura di un modello di testo](#writing).|  
    |Project Path|Specifica il percorso del progetto di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che conterrà i file di output della trasformazione. Usare valori tipizzati per creare un nuovo progetto. Fare clic sul pulsante con puntini di sospensione (**[...]** ) per selezionare un progetto esistente.<br /><br /> Se non esiste alcun progetto, verrà creato un nuovo progetto Libreria di classi C#.<br /><br /> A questo scopo, è necessario digitare direttamente il progetto. È possibile includere macro di variabili di ambiente quali %ProgramFiles% o %LocalAppData%.|  
    |Target Directory|Cartella in cui viene generato il file di destinazione. Il percorso è relativo alla cartella del progetto.<br /><br /> È possibile usare l'espressione `{PackageStructure}` per inserire un percorso che corrisponde ai nomi dei pacchetti contenitore. Il valore predefinito è `\GeneratedCode\{PackageStructure}`. È anche possibile includere variabili di ambiente quali %TEMP% o %HomePath%. **Importante:** `{PackageStructure}` può essere utilizzato solo nelle **Directory di destinazione** proprietà.|  
    |Percorso del file di modello|Modello che eseguirà la trasformazione.<br /><br /> È possibile usare i modelli forniti o crearne di personalizzati. I modelli forniti sono disponibili nel percorso seguente:<br /><br /> … \Programmi\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\|  
  
5.  È possibile collegare a un elemento il numero di associazioni desiderato.  
  
##  <a name="writing"></a> Scrittura di un modello di testo  
 È possibile scrivere modelli di testo personalizzati. I modelli di testo possono generare codice programma o qualsiasi altro tipo di file di testo.  
  
 Si consiglia di iniziare modificando copie dei modelli standard. È possibile copiare i modelli dai seguenti percorsi:  
  
 … \Programmi\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  
  
 Per comprendere i modelli di testo, fare riferimento agli argomenti seguenti.  
  
-   Un modello di testo è un prototipo del file risultante e contiene sia il testo risultante che il codice programma che legge il modello. Per altre informazioni, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).  
  
-   Per esplorare il modello UML nel codice programma, è necessario usare l'API UML. Per altre informazioni, vedere [esplorare il modello UML](../modeling/navigate-the-uml-model.md) e [riferimento all'API per l'estensibilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
 Usare i modelli con il **genera codice** comando, è necessario includere la direttiva Modeling. Ad esempio:  
  
 `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  
  
 L'attributo `ElementType` definisce il tipo di elemento UML al quale si applica il modello.  
  
 Nel modello, `this` appartiene a una classe temporanea che dispone delle proprietà seguenti:  
  
-   `Element` corrisponde all'oggetto <xref:Microsoft.VisualStudio.Uml.Classes.IElement> a cui viene applicato il modello.  
  
-   `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  
  
-   `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
-   `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. Per altre informazioni, vedere [integrare i modelli UML con altri modelli e strumenti](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   `ProfileName` corrisponde a "C#Profile".  
  
-   `ServiceProvider`: <xref:System.IServiceProvider>  
  
-   `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  
  
-   `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Si tratta dell'archivio dell'SDK di visualizzazione e modellazione sul quale viene implementato l'oggetto UML ModelStore. Per ottenere l'oggetto UML <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, usare `this.Element.GetModelStore()`.  
  
 Le informazioni seguenti possono risultare utili durante la scrittura di un modello di testo. Queste informazioni sono descritto dettagliatamente [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).  
  
-   È possibile impostare l'estensione del file risultante nella direttiva `Output`. Una direttiva `Output` è richiesta in ogni modello di testo.  
  
-   Ad alcuni assembly viene fatto automaticamente riferimento nel modello. Tali assembly includono, ad esempio, System.dll e Microsoft.VisualStudio.Uml.Interfaces.dll.  
  
     Per usare altri assembly nel codice programma generatore, è necessario usare una direttiva `Assembly`. Ad esempio:  
  
     `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  
  
-   Alcuni spazi dei nomi quali `System` vengono importati automaticamente nel codice programma. Per altri spazi dei nomi, è possibile usare la direttiva `Import` in modo analogo a un'istruzione `using`. Ad esempio:  
  
     `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  
  
     `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  
  
-   Usare la direttiva `Include` per fare riferimento al testo di un altro file.  
  
-   Le parti del modello racchiuse tra parentesi quadre `<# ... #>` vengono eseguiti per il **genera codice** comando. Le parti del modello esterne a tali parentesi vengono copiate nel file risultante. È importante distinguere tra il codice generatore e il testo generato. Il testo generato può essere in qualsiasi linguaggio.  
  
-   Le parti `<#= Expressions #>` vengono valutate e convertite in stringhe.  
  
## <a name="see-also"></a>Vedere anche  
 [Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)   
 [Generare file da un modello UML](../modeling/generate-files-from-a-uml-model.md)



