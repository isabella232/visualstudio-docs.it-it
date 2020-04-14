---
title: Creare viste personalizzate di oggetti di C++
description: Utilizzare il framework Natvis per personalizzare il modo in cui Visual Studio visualizza i tipi nativi nel debuggerUse the Natvis framework to customize the way that Visual Studio displays native types in the debugger
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224511"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Creare visualizzazioni personalizzate di oggetti in linguaggio C, usando il framework Natvis

Il framework di Visual Studio *Natvis* consente di personalizzare il modo in cui i tipi nativi vengono visualizzati nelle finestre delle variabili del debugger, ad esempio le finestre **Variabili locali** e Espressioni **di controllo,** e nei **suggerimenti dati**. Le visualizzazioni Natvis consentono di rendere i tipi creati più visibili durante il debug.

Natvis sostituisce il file *autoexp.dat* nelle versioni precedenti di Visual Studio con sintassi XML, diagnostica migliore, controllo delle versioni e supporto di più file.

> [!NOTE]
> Le personalizzazioni Natvis funzionano con classi e struct, ma non con i typedef.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Visualizzazioni Natvis

Il framework Natvis viene utilizzato per creare regole di visualizzazione per i tipi creati, in modo che gli sviluppatori possano visualizzarle più facilmente durante il debug.

Ad esempio, la figura seguente mostra una variabile di tipo [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) in una finestra del debugger senza alcuna visualizzazione personalizzata applicata.

![Visualizzazione predefinita di TextBox](../debugger/media/dbg_natvis_textbox_default.png "Visualizzazione predefinita di TextBox")

La riga evidenziata mostra la proprietà `Text` della classe `TextBox` . La gerarchia di classi complessa rende difficile trovare questa proprietà. Il debugger non sa come interpretare il tipo di stringa personalizzata, pertanto non è possibile visualizzare la stringa contenuta all'interno della casella di testo.

Lo `TextBox` stesso aspetto sembra molto più semplice nella finestra delle variabili quando vengono applicate le regole del visualizzatore personalizzato Natvis.The same looks much simpler in the variable window when Natvis custom visualizer rules are applied. I membri importanti della classe vengono visualizzati insieme e il debugger mostra il valore di stringa sottostante del tipo di stringa personalizzato.

![Dati TextBox con uso di visualizzatore](../debugger/media/dbg_natvis_textbox_visualizer.png "Dati TextBox con uso di visualizzatore")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Utilizzare i file con estensione natvis nei progetti in C

Natvis utilizza i file *.natvis* per specificare le regole di visualizzazione. Un file *.natvis* è un file XML con estensione *.natvis.* Lo schema Natvis è definito in *%VSINSTALLDIR%*.

La struttura di base di un file `Type` *.natvis* è costituita da uno o più elementi che rappresentano le voci di visualizzazione. Il nome completo `Type` di ogni elemento `Name` è specificato nel relativo attributo.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio fornisce alcuni file *con estensione natvis* nella cartella *%VSINSTALLDIR%* Questi file hanno regole di visualizzazione per molti tipi comuni e possono servire da esempio per la scrittura di visualizzazioni per nuovi tipi.

### <a name="add-a-natvis-file-to-a-c-project"></a>Aggiungere un file con estensione natvis a un progetto in linguaggio C

È possibile aggiungere un file *con estensione natvis* a qualsiasi progetto C.

**Per aggiungere un nuovo file *.natvis:***

1. Selezionare il nodo del progetto di C, in **Esplora soluzioni**, quindi selezionare **Aggiunta** > **nuovo elemento**, oppure fare clic con il pulsante destro del mouse sul progetto e **scegliere Aggiungi** > **nuovo elemento**.

1. Nella finestra di dialogo **Aggiungi nuovo elemento** , selezionare il file di visualizzazione del debugger**dell'utilità** > **di** **Visual C** > 

1. Assegnare un nome al file e selezionare **Aggiungi**.

   Il nuovo file viene aggiunto a **Esplora soluzioni**e viene aperto nel riquadro del documento di Visual Studio.

Il debugger di Visual Studio carica automaticamente i file *con estensione natvis* nei progetti in C, e, per impostazione predefinita, li include anche nel file *con estensione pdb* durante la compilazione del progetto. Se esegui il debug dell'app compilata, il debugger carica il file *con estensione natvis* dal file *con estensione pdb,* anche se il progetto non è aperto. Se non si desidera che il file *natvis* venga incluso nel file *pdb*, è possibile escluderlo dal file *con estensione pdb* compilato.

**Per escludere un file *.natvis* da un *file .pdb*:**

1. Selezionare il file *natvis* in **Esplora soluzioni**, quindi selezionare l'icona **Proprietà** oppure fare clic con il pulsante destro del mouse sul file e scegliere **Proprietà**.

1. Fare clic sulla freccia accanto a **Escluso dalla compilazione** e selezionare **Sì**, quindi **scegliere OK**.

>[!NOTE]
>Per il debug di progetti eseguibili, utilizzare gli elementi della soluzione per aggiungere i file *con estensione natvis* che non si trovano nel file *pdb*, poiché non è disponibile alcun progetto C.

>[!NOTE]
>Le regole Natvis caricate da un *file pdb* si applicano solo ai tipi nei moduli a cui fa riferimento il *file con estensione pdb.* Ad esempio, se *Module1.pdb* dispone di una `Test`voce Natvis `Test` per un tipo denominato , si applica solo alla classe in *Module1.dll*. Se un altro modulo definisce anche una classe denominata `Test`, la voce *Module1.pdb* Natvis non si applica ad essa.

**Per installare e registrare un file *.natvis* tramite un pacchetto VSIX:**

Un pacchetto VSIX può installare e registrare i file *con estensione natvis.* Indipendentemente da dove sono installati, tutti i file *.natvis* registrati vengono raccolti automaticamente durante il debug.

1. Includere il file *natvis* nel pacchetto VSIX. Ad esempio, per il file di progetto seguente:For example, for the following project file:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Registrare il file *natvis* nel file *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Posizioni dei file Natvis

È possibile aggiungere file *.natvis* alla directory utente o a una directory di sistema, se si desidera applicarli a più progetti.

I file *.natvis* vengono valutati nel seguente ordine:

1. Tutti i file *con estensione natvis* incorporati in un *file con estensione pdb* di cui si esegue il debug, a meno che nel progetto caricato non sia presente un file con lo stesso nome.

2. Tutti i file *con estensione natvis* che si trovano in un progetto di tipo c'è caricato o in una soluzione di primo livello. Questo gruppo include tutti i progetti caricati in C, incluse le librerie di classi, ma non i progetti in altri linguaggi.

3. Qualsiasi file *con estensione natvis* installato e registrato tramite un pacchetto VSIX.

::: moniker range="vs-2017"

4. La directory Natvis specifica dell'utente (ad esempio, *%USERPROFILE%*.

::: moniker-end

::: moniker range=">= vs-2019"

4. La directory Natvis specifica dell'utente (ad esempio, *%USERPROFILE%*.

::: moniker-end

5. La directory Natvis a livello di sistema (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Questa directory contiene i file *con estensione natvis* installati con Visual Studio. Se si dispone delle autorizzazioni di amministratore, è possibile aggiungere file a questa directory.

## <a name="modify-natvis-files-while-debugging"></a>Modificare i file .natvis durante il debug

È possibile modificare un file *con estensione natvis* nell'IDE durante il debug del progetto. Aprire il file nella stessa istanza di Visual Studio con cui si esegue il debug, modificarlo e salvarlo. Non appena il file viene salvato, le finestre **Espressioni** di controllo e **Variabili locali** vengono aggiornate per riflettere la modifica.

È inoltre possibile aggiungere o eliminare file *con estensione natvis* in una soluzione di cui si sta eseguendo il debug e Visual Studio aggiunge o rimuove le visualizzazioni pertinenti.

Non è possibile aggiornare i file *con estensione natvis* incorporati nei file *pdb* durante il debug.

Se si modifica il file *con estensione natvis* all'esterno di Visual Studio, le modifiche non hanno effetto automatico. Per aggiornare le finestre del debugger, è possibile rivalutare il comando **.natvisreload** nella finestra **Immediata.** Quindi le modifiche diventano effettive senza riavviare la sessione di debug.

Utilizzare anche il comando **.natvisreload** per aggiornare il file *natvis* a una versione più recente. Ad esempio, il file *.natvis* può essere archiviato nel controllo del codice sorgente e si desidera raccogliere le modifiche recenti apportate da un altro utente.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Espressioni e formattazione
Nelle visualizzazioni Natvis si usano espressioni C++ per specificare gli elementi di dati da visualizzare. Oltre ai miglioramenti e alle limitazioni delle espressioni c'è nel debugger, descritti in Operatore di [contesto (C)](../debugger/context-operator-cpp.md), tenere presente quanto segue:

- Le espressioni di Natvis vengono valutate nel contesto dell'oggetto da visualizzare, non nello stack frame corrente. Ad esempio, `x` in un'espressione Natvis si riferisce al campo denominato **x** nell'oggetto visualizzato, non a una variabile locale denominata **x** nella funzione corrente. Non è possibile accedere alle variabili locali nelle espressioni Natvis, sebbene sia possibile accedere alle variabili globali.

- Le espressioni Natvis non consentono la valutazione della funzione o effetti collaterali. Le chiamate di funzione e gli operatori di assegnazione vengono ignorati. Dal momento che le [funzioni intrinseche del debugger](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) non hanno effetti collaterali, possono essere chiamate liberamente da qualsiasi espressione Natvis, anche se non sono consentite altre chiamate di funzione.

- Per controllare la modalità di visualizzazione di un'espressione, è possibile utilizzare uno qualsiasi degli identificatori di formato descritti in Identificatori di [formato in C.](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) Gli identificatori di formato vengono ignorati quando la voce `Size` viene utilizzata internamente da Natvis, ad esempio l'espressione in un'espansione [ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Visualizzazioni di Natvis

È possibile definire diverse viste Natvis per visualizzare i tipi in modi diversi. Ad esempio, di seguito `std::vector` è riportata una `simple`visualizzazione di che definisce una visualizzazione semplificata denominata . Gli `DisplayString` elementi `ArrayItems` e vengono visualizzati `simple` nella visualizzazione `[size]` predefinita `[capacity]` e nella visualizzazione, `simple` mentre gli elementi e non vengono visualizzati nella visualizzazione.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Nella finestra **Espressioni di controllo,** utilizzare l'identificatore di formato **,view** per specificare una visualizzazione alternativa. La vista semplice appare come **vec,view(simple)**:

![Finestra Espressioni di controllo con visualizzazione semplice](../debugger/media/watch-simpleview.png "Finestra Espressioni di controllo con visualizzazione semplice")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Errori di Natvis

Quando il debugger rileva errori in una voce di visualizzazione, li ignora. Visualizza il tipo nella sua forma grezza o sceglie un'altra visualizzazione appropriata. È possibile utilizzare la diagnostica Natvis per comprendere il motivo per cui il debugger ha ignorato una voce di visualizzazione e per visualizzare gli errori di sintassi e di analisi sottostanti.

**Per attivare la diagnostica Natvis:**

- In**Opzioni** **degli strumenti** > (o**Opzioni** **di debug** > ) >**Finestra di output**di **debug** > , impostare i **messaggi di diagnostica Natvis (solo C) su** **Errore**, **Avviso**o **Dettagliato**, quindi scegliere **OK**.

Gli errori vengono visualizzati nella finestra **Output.The errors** appear in the Output window.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Riferimento per la sintassi di Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer
L'elemento `AutoVisualizer` è il nodo radice del file *NATVIS* e contiene l'attributo `xmlns:` dello spazio dei nomi.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

L'elemento `AutoVisualizer` può avere elementi figlio [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)e [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="type-element"></a><a name="BKMK_Type"></a>Elemento Type

Un `Type` aspetto di base simile a questo esempio:A basic looks like this example:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 L'elemento `Type` specifica:

1. Per quale tipo deve essere `Name` utilizzata la visualizzazione (attributo).

2. A quale valore di un oggetto di tale tipo deve essere simile (elemento `DisplayString` ).

3. Aspetto dei membri del tipo quando l'utente espande il tipo `Expand` in una finestra delle variabili (nodo).

#### <a name="templated-classes"></a>Classi basate su modelli
`Name` L'attributo `Type` dell'elemento `*` accetta un asterisco come carattere jolly che può essere utilizzato per i nomi delle classi basate su modelli.

Nell'esempio seguente viene utilizzata la stessa visualizzazione `CAtlArray<int>` indipendentemente dal fatto che l'oggetto sia a o un `CAtlArray<float>`oggetto . Se è presente una voce `CAtlArray<float>`di visualizzazione specifica per un oggetto , ha la precedenza su quella generica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

È possibile fare riferimento ai parametri del modello nella voce di visualizzazione utilizzando le macro $T1, $T2 e così via. Per esempi di queste macro, vedere i file *NATVIS* forniti con Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Corrispondenza del tipo di visualizzatore
Se la convalida di una voce di visualizzazione non riesce, viene utilizzata la successiva visualizzazione disponibile.

#### <a name="inheritable-attribute"></a>Attributo Inheritable
L'attributo facoltativo `Inheritable` specifica se una visualizzazione si applica solo a un tipo di base o a un tipo di base e a tutti i tipi derivati. Il valore predefinito di `Inheritable` è `true`.

Nell'esempio seguente, la visualizzazione `BaseClass` si applica solo al tipo:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Attributo Priority

L'attributo optional `Priority` specifica l'ordine in cui utilizzare le definizioni alternative, se una definizione non riesce ad analizzare. I valori `Priority` possibili `Low`di `MediumLow``Medium`sono: , , , `MediumHigh`, e `High`. Il valore predefinito è `Medium`. L'attributo `Priority` distingue solo tra le priorità all'interno dello stesso file *.natvis.*

Nell'esempio seguente viene innanzitutto analizzato la voce che corrisponde alla STL 2015. Se l'analisi non riesce, viene utilizzata la voce alternativa per la versione 2013 di STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Attributo Optional
È possibile `Optional` inserire un attributo in qualsiasi nodo. Se una sottoespressione all'interno di un nodo facoltativo non viene analizzata, il debugger ignora tale nodo, ma applica le altre `Type` regole. Nel tipo seguente `[State]` non è facoltativo, mentre `[Exception]` lo è.  Se `MyNamespace::MyClass` è presente`M_exceptionHolder`un campo `[State]` denominato `[Exception]` _ , il nodo e `_M_exceptionHolder` il nodo `[State]` vengono visualizzati, ma se non è presente alcun campo, verrà visualizzato solo il nodo.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Attributo Condition

L'attributo facoltativo `Condition` è disponibile per molti elementi di visualizzazione e specifica quando utilizzare una regola di visualizzazione. Se l'espressione all'interno `false`dell'attributo condition viene risolta in , la regola di visualizzazione non viene applicata. Se restituisce `true`o non è `Condition` presente alcun attributo, viene applicata la visualizzazione. È possibile utilizzare questo attributo per la logica if-else nelle voci di visualizzazione.

Ad esempio, la visualizzazione `DisplayString` seguente include due elementi per un tipo di puntatore intelligente. Quando `_Myptr` il membro è vuoto, `DisplayString` la condizione `true`del primo elemento viene risolta in , in modo che venga visualizzato il form. Quando `_Myptr` il membro non è vuoto, `false`la condizione `DisplayString` restituisce e viene visualizzato il secondo elemento.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>Attributi IncludeView e ExcludeView

Gli `IncludeView` `ExcludeView` attributi e specificano gli elementi da visualizzare o meno in viste specifiche. Ad esempio, nella seguente specifica `std::vector`Natvis di , la `simple` visualizzazione non visualizza gli `[size]` elementi e `[capacity]` .

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

È possibile `IncludeView` utilizzare `ExcludeView` gli attributi e sui tipi e sui singoli membri.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Elemento Version
L'elemento `Version` ambito una voce di visualizzazione a un modulo e una versione specifici. L'elemento `Version` consente di evitare conflitti di nomi, riduce le mancate corrispondenze involontarie e consente visualizzazioni diverse per versioni di tipo diverso.

Se un file di intestazione comune utilizzato da moduli diversi definisce un tipo, la visualizzazione con controllo delle versioni viene visualizzata solo quando il tipo si trova nella versione del modulo specificata.

Nell'esempio seguente, la visualizzazione è `DirectUI::Border` applicabile solo `Windows.UI.Xaml.dll` per il tipo trovato nella versione 1.0 alla 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Non hai bisogno `Min` di `Max`entrambi e . Sono attributi facoltativi. Non sono supportati caratteri jolly.

L'attributo `Name` è nel formato *nomefile.ext*, ad esempio *hello.exe* o *some.dll*. Non sono consentiti nomi di percorso.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>DisplayString (elemento)
L'elemento `DisplayString` specifica una stringa da visualizzare come valore di una variabile. Accetta stringhe arbitrarie combinate con espressioni. Tutto ciò che è racchiuso tra parentesi graffe viene interpretato come un'espressione. Ad esempio, `DisplayString` la seguente voce:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Significa che le `CPoint` variabili di tipo vengono visualizzate come in questa illustrazione:

 ![Utilizzare un displayString elemento](../debugger/media/dbg_natvis_cpoint_displaystring.png "Utilizzare un displayString elemento")

`DisplayString` Nell'espressione, `x` `y`e , che `CPoint`sono membri di , sono all'interno di parentesi graffe, pertanto i relativi valori vengono valutati. Nell'esempio viene inoltre illustrato come eseguire l'escape di una `{{` `}}` parentesi graffa utilizzando parentesi graffe doppie ( o ).

> [!NOTE]
> L'elemento `DisplayString` è l'unico elemento che accetta stringhe arbitrarie e la sintassi con parentesi graffe. Tutti gli altri elementi di visualizzazione accettano solo espressioni che il debugger può valutare.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>StringView (elemento)

L'elemento `StringView` definisce un valore che il debugger può inviare al visualizzatore di testo incorporato. Ad esempio, data la `ATL::CStringT` seguente visualizzazione per il tipo:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

L'oggetto `CStringT` viene visualizzato in una finestra delle variabili come questo esempio:The object displays in a variable window like this example:

![Elemento DisplayString CStringT](../debugger/media/dbg_natvis_displaystring_cstringt.png "Elemento DisplayString CStringT")

L'aggiunta di un `StringView` elemento indica al debugger che può visualizzare il valore come visualizzazione di testo.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante il debug, è possibile selezionare l'icona della lente di ingrandimento accanto alla variabile e quindi selezionare **Visualizzatore di testo** per visualizzare la stringa a cui **m_pszData** punta.

 ![Dati CStringT con visualizzatore StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Dati CStringT con visualizzatore StringView")

L'espressione `{m_pszData,su}` include un identificatore di formato di C , **su**, per visualizzare il valore come stringa Unicode. Per ulteriori informazioni, consultate Identificatori di [formato in C.](../debugger/format-specifiers-in-cpp.md)

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Espandi elemento

Il `Expand` nodo facoltativo personalizza gli elementi figlio di un tipo visualizzato quando si espande il tipo in una finestra di variabile. Il `Expand` nodo accetta un elenco di nodi figlio che definiscono gli elementi figlio.

- Se `Expand` un nodo non è specificato in una voce di visualizzazione, gli elementi figlio utilizzano le regole di espansione predefinite.

- Se `Expand` viene specificato un nodo senza nodi figlio, il tipo non è espandibile nelle finestre del debugger.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Espansione di Item

 L'elemento `Item` è l'elemento più `Expand` semplice e comune in un nodo. `Item` definisce un singolo elemento figlio. Ad esempio, `CRect` una `top`classe `left` `right`con `bottom` campi , , e ha la seguente voce di visualizzazione:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Nella finestra del `CRect` debugger il tipo è simile all'esempio seguente:In the debugger window, the type looks like this example:

![CRect con espansione dell'elemento Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect con espansione dell'elemento Item")

Il debugger valuta le espressioni `Width` `Height` specificate negli elementi e e mostra i valori nella colonna **Valore** della finestra delle variabili.

Il debugger crea automaticamente il nodo **[Raw View]** per ogni espansione personalizzata. Nella schermata precedente viene visualizzato il nodo **[Raw View]** espanso, per mostrare come la visualizzazione non elaborata predefinita dell'oggetto differisca dalla visualizzazione Natvis. L'espansione predefinita crea un sottoalbero per la classe base ed elenca tutti i membri dati della classe base come elementi figlio.

> [!NOTE]
> Se l'espressione dell'elemento item punta a un tipo complesso, il nodo **Item** stesso è espandibile.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Usare il nodo `ArrayItems` per consentire al debugger di Visual Studio di interpretare il tipo come una matrice e visualizzarne i singoli elementi. La visualizzazione per `std::vector` costituisce un ottimo esempio:

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

Un elemento `std::vector` visualizza i singoli elementi quando viene espanso nella finestra delle variabili:

![std::vector con uso dell'espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector con uso dell'espansione ArrayItems")

Il `ArrayItems` nodo deve avere:

- Un'espressione `Size` (che deve restituire un numero intero) per consentire al debugger di riconoscere la lunghezza della matrice.
- Espressione `ValuePointer` che punta al primo elemento (che deve essere un `void*`puntatore di un tipo di elemento diverso).

Il valore predefinito del limite inferiore della matrice è 0. Per eseguire l'override `LowerBound` del valore, utilizzare un elemento. I file *.natvis* forniti con Visual Studio hanno esempi.

>[!NOTE]
>È possibile `[]` utilizzare l'operatore, ad esempio `vector[i]`, `ArrayItems`con qualsiasi visualizzazione matrice unidimensionale che utilizza , anche se il tipo stesso (ad esempio `CATLArray`) non consente questo operatore.

È inoltre possibile specificare matrici multidimensionali. In tal caso, il debugger necessita di ulteriori informazioni per visualizzare correttamente gli elementi figlio:In that case, the debugger needs slightly more information to display properly child elements:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`specifica se la matrice è in ordine di riga o colonna maggiore.
- `Rank` specifica l'ordine di priorità della matrice.
- L'elemento `Size` accetta il parametro `$i` implicito che sostituisce con l'indice delle dimensioni per individuare la lunghezza della matrice in quella dimensione. Nell'esempio precedente, `_M_extent.M_base[0]` l'espressione deve restituire la `_M_extent._M_base[1]` lunghezza della dimensione 0, la prima e così via.

Ecco come appare un `Concurrency::array` oggetto bidimensionale nella finestra del debugger:Here's how a two-dimensional object looks in the debugger window:

![Matrice bidimensionale con espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Matrice bidimensionale con espansione ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Espansione di IndexListItems

È possibile `ArrayItems` utilizzare l'espansione solo se gli elementi della matrice sono disposti in modo contiguo in memoria. Il debugger passa all'elemento successivo semplicemente incrementando il puntatore. Se è necessario modificare l'indice per `IndexListItems` il nodo valore, utilizzare i nodi. Ecco una visualizzazione con `IndexListItems` un nodo:Here's a visualization with an node:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

L'unica `ArrayItems` differenza `IndexListItems` tra `ValueNode`e è il , che prevede l'espressione completa per l'elemento i<sup>th</sup> con il parametro implicit. `$i`

>[!NOTE]
>È possibile `[]` utilizzare l'operatore, ad esempio `vector[i]`, `IndexListItems`con qualsiasi visualizzazione matrice unidimensionale che utilizza , anche se il tipo stesso (ad esempio `CATLArray`) non consente questo operatore.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Espansione di LinkedListItems

Se il tipo visualizzato rappresenta un elenco collegato, il debugger può visualizzarne i figli tramite un nodo `LinkedListItems` . La seguente visualizzazione `CAtlList` per `LinkedListItems`il tipo utilizza:

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

L'elemento `Size` si riferisce alla lunghezza dell'elenco. `HeadPointer` punta al primo elemento, `NextPointer` fa riferimento all'elemento successivo e `ValueNode` fa riferimento al valore dell'elemento.

Il debugger valuta `NextPointer` `ValueNode` le espressioni e `LinkedListItems` nel contesto dell'elemento nodo, non il tipo di elenco padre. Nell'esempio precedente, `CAtlList` include `CNode` una classe `atlcoll.h`(trovata in ) che è un nodo dell'elenco collegato. `m_pNext`e `m_element` sono campi `CNode` di quella `CAtlList` classe, non della classe.

`ValueNode`può essere lasciato vuoto, o `this` `LinkedListItems` utilizzare per fare riferimento al nodo stesso.

#### <a name="customlistitems-expansion"></a>Espansione CustomListItems

L'espansione `CustomListItems` consente di scrivere una logica personalizzata per attraversare una struttura dei dati, ad esempio una tabella hash. Utilizzare `CustomListItems` per visualizzare le strutture di dati che possono utilizzare le espressioni di C, `ArrayItems` `IndexListItems`per `LinkedListItems`tutto ciò che è necessario valutare, ma non si adattano perfettamente allo stampo per , , o .

È possibile `Exec` utilizzare per eseguire `CustomListItems` codice all'interno di un'espansione, utilizzando le variabili e gli oggetti definiti nell'espansione. È possibile utilizzare operatori logici, operatori `Exec`aritmetici e operatori di assegnazione con . Non è possibile `Exec` utilizzare per valutare le funzioni, ad eccezione delle [funzioni intrinseche](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) del debugger supportate dall'analizzatore di espressioni di C.

Il visualizzatore `CAtlMap` seguente per è `CustomListItems` un ottimo esempio, se appropriato.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Espansione di TreeItems
 Se il tipo visualizzato rappresenta un albero, il debugger può esaminare l'albero e visualizzarne i figli tramite un nodo `TreeItems` . Di seguito è riportata la visualizzazione per il tipo che utilizza un nodo:Here's the visualization for the `std::map` type using a `TreeItems` node:

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

La sintassi è `LinkedListItems` simile al nodo. `LeftPointer`, `RightPointer`, `ValueNode` e vengono valutati nel contesto della classe del nodo della struttura ad albero. `ValueNode`può essere lasciato `this` vuoto o `TreeItems` utilizzare per fare riferimento al nodo stesso.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Espansione di ExpandedItem
 L'elemento `ExpandedItem` genera una visualizzazione figlio aggregata visualizzando le proprietà delle classi di base o dei membri dati come se fossero elementi figlio del tipo visualizzato. Il debugger valuta l'espressione specificata e aggiunge i nodi figlio del risultato all'elenco figlio del tipo visualizzato.

Ad esempio, il `auto_ptr<vector<int>>` tipo di puntatore intelligente viene in genere visualizzato come:

 ![auto&#95;ptr&#60;vettore&#60;int&#62;&#62; espansione predefinita](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Espansione predefinita")

 Per visualizzare i valori del vettore, è necessario eseguire il drill-down di due livelli nella finestra delle variabili, passando attraverso il `_Myptr` membro. Aggiungendo un elemento `ExpandedItem`, è possibile eliminare la variabile `_Myptr` dalla gerarchia e visualizzare direttamente gli elementi del vettore:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;vettore di&#60;ptr&#60;int&#62;&#62; espansione ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Espansione di ExpandedItem")

Nell'esempio seguente viene illustrato come aggregare le proprietà dalla classe base in una classe derivata. Si supponga che la classe `CPanel` derivi da `CFrameworkElement`. Anziché ripetere le proprietà che `CFrameworkElement` provengono `ExpandedItem` dalla classe base, la visualizzazione `CPanel` del nodo aggiunge tali proprietà all'elenco figlio della classe.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

In questo caso è necessario l'identificatore di formato **nd** che disattiva la corrispondenza della visualizzazione per la classe derivata. In caso `*(CFrameworkElement*)this` contrario, `CPanel` l'espressione causerebbe nuovamente l'applicazione della visualizzazione, poiché le regole di corrispondenza del tipo di visualizzazione predefinito la considerano la più appropriata. Utilizzare l'identificatore di formato **nd** per indicare al debugger di utilizzare la visualizzazione della classe base o l'espansione predefinita se la classe base non dispone di alcuna visualizzazione.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Espansione degli elementi sintetici
 Il nodo `ExpandedItem` esegue la funzione opposta rispetto all'elemento `Synthetic`, che fornisce una visualizzazione dei dati più semplice eliminando le gerarchie. Consente di creare un elemento figlio artificiale che non è il risultato di un'espressione. L'elemento artificiale può avere elementi figlio propri. Nell'esempio seguente nella visualizzazione del tipo `Concurrency::array` viene usato un nodo `Synthetic` per mostrare un messaggio di diagnostica all'utente:

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concorrenza::Matrice con espansione di elementi sinteticiConcurrency::Array with Synthetic element expansion](../debugger/media/dbg_natvis_expand_synthetic.png "Concorrenza::Matrice con espansione di elementi sinteticiConcurrency::Array with Synthetic element expansion")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>Elemento HResult
 L'elemento `HResult` consente di personalizzare le informazioni visualizzate per **un HRESULT** nelle finestre del debugger. L'elemento `HRValue` deve contenere il valore a 32 bit di **HRESULT** da personalizzare. L'elemento `HRDescription` contiene le informazioni da visualizzare nella finestra del debugger.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>Elemento UIVisualizer
Un elemento `UIVisualizer` consente di registrare un plug-in del visualizzatore grafico con il debugger. Un visualizzatore grafico crea una finestra di dialogo o un'altra interfaccia che mostra una variabile o un oggetto in modo coerente con il relativo tipo di dati. Il plug-in del visualizzatore deve essere creato come [VSPackage](../extensibility/internals/vspackages.md)e deve esporre un servizio che il debugger può utilizzare. Il file *natvis* contiene informazioni di registrazione per il plug-in, ad esempio il nome, il GUID del servizio esposto e i tipi che è possibile visualizzare.

Il seguente è un esempio di elemento UIVisualizer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- `ServiceId`  -  Una `Id` coppia di `UIVisualizer`attributi identifica un file . Il `ServiceId` è il GUID del servizio esposto dal pacchetto del visualizzatore. `Id`è un identificatore univoco che differenzia i visualizzatori, se un servizio ne fornisce più di uno. Nell'esempio precedente, lo stesso servizio visualizzatore fornisce due visualizzatori.

- L'attributo `MenuName` definisce un nome del visualizzatore da visualizzare nell'elenco a discesa accanto all'icona della lente di ingrandimento nel debugger. Ad esempio:

  ![Menu di scelta rapida UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu di scelta rapida UIVisualizer")

Ogni tipo definito nel file *.natvis* deve elencare in modo esplicito tutti i visualizzatori dell'interfaccia utente che possono visualizzarlo. Il debugger corrisponde ai riferimenti del visualizzatore nelle voci di tipo con i visualizzatori registrati. Ad esempio, la seguente `std::vector` voce `UIVisualizer` di tipo per fa riferimento a nell'esempio precedente.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 È possibile visualizzare un `UIVisualizer` esempio di un nell'estensione Espressioni di [controllo immagine](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) utilizzata per visualizzare le bitmap in memoria.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Elemento CustomVisualizer
 `CustomVisualizer`è un punto di estendibilità che specifica un'estensione VSIX scritta per controllare le visualizzazioni nel codice di Visual Studio.Is an extensibility point that specifies a VSIX extension that you write to control visualizations in Visual Studio code. Per ulteriori informazioni sulla scrittura di estensioni VSIX, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

È molto più lavoro per scrivere un visualizzatore personalizzato rispetto a una definizione di NATvis XML, ma sei libero da vincoli su ciò che Natvis fa o non supporta. I visualizzatori personalizzati hanno accesso al set completo di API di estendibilità del debugger, che possono eseguire query e modificare il processo dell'oggetto del debug o comunicare con altre parti di Visual Studio.Custom visualizers have access to the full set of debugger extensibility APIs, which can query and modify the debuggee process or communicate with other parts of Visual Studio.

 È possibile `Condition`utilizzare `IncludeView`gli `ExcludeView` attributi `CustomVisualizer` , e sugli elementi.

 ## <a name="limitations"></a>Limitazioni

Le personalizzazioni Natvis funzionano con classi e struct, ma non con i typedef.

Natvis non supporta i visualizzatori per i `int` `bool`tipi primitivi( ad esempio, , ) o per i puntatori a tipi primitivi. In questo scenario, un'opzione consiste nell'utilizzare [l'identificatore](../debugger/format-specifiers-in-cpp.md) di formato appropriato per il caso di utilizzo. Ad esempio, se `double* mydoublearray` si utilizza nel codice, è possibile utilizzare un identificatore di formato `mydoublearray, [100]`di matrice nella finestra **Espressioni** di controllo del debugger, ad esempio l'espressione , che mostra i primi 100 elementi.
