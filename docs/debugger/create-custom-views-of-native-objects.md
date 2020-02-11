---
title: Creare viste personalizzate di oggetti di C++
description: Usare il Framework natvis per personalizzare il modo in cui Visual Studio Visualizza i tipi nativi nel debugger
ms.date: 10/31/2018
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
ms.openlocfilehash: 61a8cce68a55f6db26de7754bdfc9dda196c457a
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091782"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Creare visualizzazioni personalizzate di C++ oggetti nel debugger usando il Framework natvis

Il Framework *natvis* di Visual Studio Personalizza la modalità di visualizzazione dei tipi nativi nelle finestre delle variabili del debugger, ad esempio le finestre variabili **locali** e **espressioni di controllo** e nei **suggerimenti**dati. Le visualizzazioni di natvis consentono di rendere più visibili i tipi creati durante il debug.

Natvis sostituisce il file *autoexp. dat* nelle versioni precedenti di Visual Studio con sintassi XML, migliore diagnostica, controllo delle versioni e supporto di più file.

> [!NOTE]
> Le personalizzazioni di natvis funzionano con classi e struct, ma non con typedef.

## <a name="BKMK_Why_create_visualizations_"></a>Visualizzazioni di natvis

Usare il Framework natvis per creare regole di visualizzazione per i tipi creati, in modo che gli sviluppatori possano visualizzarli più facilmente durante il debug.

Nell'illustrazione seguente, ad esempio, viene mostrata una variabile di tipo [Windows:: UI:: XAML:: Controls:: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) in una finestra del debugger senza alcuna visualizzazione personalizzata applicata.

![Visualizzazione predefinita casella di testo](../debugger/media/dbg_natvis_textbox_default.png "Visualizzazione predefinita di TextBox")

La riga evidenziata mostra la proprietà `Text` della classe `TextBox` . La gerarchia di classi complesse rende difficile trovare questa proprietà. Il debugger non è in grado di interpretare il tipo di stringa personalizzato, pertanto non è possibile visualizzare la stringa contenuta nella casella di testo.

Lo stesso `TextBox` sembra molto più semplice nella finestra delle variabili quando vengono applicate le regole del visualizzatore personalizzato natvis. I membri importanti della classe vengono visualizzati insieme e il debugger Mostra il valore stringa sottostante del tipo di stringa personalizzato.

![Dati TextBox tramite Visualizzatore](../debugger/media/dbg_natvis_textbox_visualizer.png "Dati TextBox con uso di visualizzatore")

## <a name="BKMK_Using_Natvis_files"></a>Usare i file con estensione C++ natvis nei progetti

Natvis usa i file *natvis* per specificare le regole di visualizzazione. Un file con estensione *natvis* è un file XML con estensione *natvis* . Lo schema natvis è definito in *%VSInstallDir%\Xml\Schemas\natvis.xsd*.

La struttura di base di un file con *estensione natvis* è costituita da uno o più elementi `Type` che rappresentano le voci di visualizzazione. Il nome completo di ogni elemento `Type` viene specificato nell'attributo `Name`.

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

Visual Studio fornisce alcuni file *natvis* nella cartella *%VSInstallDir%\Common7\Packages\Debugger\Visualizers* . Questi file contengono regole di visualizzazione per molti tipi comuni e possono fungere da esempi per la scrittura di visualizzazioni per nuovi tipi.

### <a name="add-a-natvis-file-to-a-c-project"></a>Aggiungere un file con estensione natvis a C++ un progetto

È possibile aggiungere un file con *estensione natvis* a C++ qualsiasi progetto.

**Per aggiungere un nuovo file con *estensione natvis* :**

1. Selezionare il C++ nodo del progetto in **Esplora soluzioni**e selezionare **progetto** > **Aggiungi nuovo elemento**oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi** > **nuovo elemento**.

1. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Visual C++**  > **Utility** > **file di visualizzazione debugger (. natvis)** .

1. Assegnare un nome al file e selezionare **Aggiungi**.

   Il nuovo file verrà aggiunto al **Esplora soluzioni**e verrà aperto nel riquadro del documento di Visual Studio.

Il debugger di Visual Studio carica automaticamente i file C++ con *estensione natvis* nei progetti e, per impostazione predefinita, li include nel file con *estensione PDB* quando il progetto viene compilato. Se si esegue il debug dell'app compilata, il debugger carica il file con *estensione natvis* dal file con *estensione PDB* anche se il progetto non è aperto. Se non si desidera che il file con *estensione natvis* sia incluso nel file *PDB*, è possibile escluderlo dal file *PDB* compilato.

**Per escludere un file con estensione *natvis* da un file *PDB*:**

1. Selezionare il file con *estensione natvis* in **Esplora soluzioni**, quindi selezionare l'icona **proprietà** oppure fare clic con il pulsante destro del mouse sul file e scegliere **Proprietà**.

1. A discesa della freccia accanto a **escluso da compila** , selezionare **Sì**e quindi fare clic su **OK**.

>[!NOTE]
>Per il debug di progetti eseguibili, usare gli elementi della soluzione per aggiungere eventuali file con *estensione natvis* che non si trovano nel file *PDB*, poiché non è disponibile alcun C++ progetto.

>[!NOTE]
>Le regole natvis caricate da un file *PDB* si applicano solo ai tipi nei moduli a cui fa riferimento il file *PDB* . Ad esempio, se *Module1. pdb* contiene una voce natvis per un tipo denominato `Test`, si applica solo alla classe `Test` in *Module1. dll*. Se un altro modulo definisce anche una classe denominata `Test`, la voce natvis di *Module1. pdb* non si applica a tale classe.

### <a name="BKMK_natvis_location"></a>Percorsi file natvis

È possibile aggiungere i file *natvis* alla directory utente o a una directory di sistema, se si desidera che vengano applicati a più progetti.

I file con *estensione natvis* vengono valutati nell'ordine seguente:

1. Tutti i file con *estensione natvis* incorporati in un file *PDB* di cui si esegue il debug, a meno che non esista un file con lo stesso nome nel progetto caricato.

2. Tutti i file con *estensione natvis* che si trovano C++ in un progetto caricato o in una soluzione di primo livello. Questo gruppo include tutti i C++ progetti caricati, incluse le librerie di classi, ma non i progetti in altre lingue.

::: moniker range="vs-2017"

3. La directory natvis specifica dell'utente (ad esempio, *%USERPROFILE%\Documents\Visual Studio 2017 \ Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

3. La directory natvis specifica dell'utente (ad esempio, *%USERPROFILE%\Documents\Visual Studio 2019 \ Visualizers*).

::: moniker-end

4. La directory Natvis a livello di sistema ( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Questa directory contiene i file *natvis* installati con Visual Studio. Se si dispone di autorizzazioni di amministratore, è possibile aggiungere file a questa directory.

## <a name="modify-natvis-files-while-debugging"></a>Modificare i file natvis durante il debug

È possibile modificare un file *natvis* nell'IDE durante il debug del progetto. Aprire il file nella stessa istanza di Visual Studio con cui si esegue il debug, modificarlo e salvarlo. Non appena il file viene salvato, le finestre **espressioni di controllo** e **variabili locali** vengono aggiornate in modo da riflettere la modifica.

È anche possibile aggiungere o eliminare file con *estensione natvis* in una soluzione di cui si sta eseguendo il debug e Visual Studio aggiunge o rimuove le visualizzazioni pertinenti.

Non è possibile aggiornare i file con *estensione natvis* incorporati nei file *PDB* durante il debug.

Se si modifica il file con *estensione natvis* all'esterno di Visual Studio, le modifiche non vengono applicate automaticamente. Per aggiornare le finestre del debugger, è possibile rivalutare il comando **. natvisreload** nella finestra **espressioni di controllo** . Quindi, le modifiche diventano effettive senza riavviare la sessione di debug.

Usare anche il comando **. natvisreload** per aggiornare il file con *estensione natvis* a una versione più recente. Il file con *estensione natvis* , ad esempio, può essere archiviato nel controllo del codice sorgente e si desidera rilevare le modifiche recenti apportate da altri utenti.

## <a name="BKMK_Expressions_and_formatting"></a> Espressioni e formattazione
Nelle visualizzazioni Natvis si usano espressioni C++ per specificare gli elementi di dati da visualizzare. Oltre ai miglioramenti e alle limitazioni delle C++ espressioni nel debugger, descritti in operatore di [contesto (C++)](../debugger/context-operator-cpp.md), tenere presente quanto segue:

- Le espressioni di Natvis vengono valutate nel contesto dell'oggetto da visualizzare, non nello stack frame corrente. `x` in un'espressione natvis, ad esempio, fa riferimento al campo denominato **x** nell'oggetto visualizzato, non a una variabile locale denominata **x** nella funzione corrente. Non è possibile accedere alle variabili locali nelle espressioni natvis, anche se è possibile accedere alle variabili globali.

- Le espressioni natvis non consentono la valutazione di funzioni o effetti collaterali. Le chiamate di funzione e gli operatori di assegnazione vengono ignorati. Dal momento che le [funzioni intrinseche del debugger](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) non hanno effetti collaterali, possono essere chiamate liberamente da qualsiasi espressione Natvis, anche se non sono consentite altre chiamate di funzione.

- Per controllare la modalità di visualizzazione di un'espressione, è possibile usare uno qualsiasi degli identificatori di formato descritti in [identificatori di formato in C++ ](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Gli identificatori di formato vengono ignorati quando la voce viene utilizzata internamente da natvis, ad esempio l'espressione `Size` in un' [espansione ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Visualizzazioni di Natvis

È possibile definire viste natvis diverse per visualizzare i tipi in modi diversi. Ecco, ad esempio, una visualizzazione di `std::vector` che definisce una visualizzazione semplificata denominata `simple`. Gli elementi `DisplayString` e `ArrayItems` vengono visualizzati nella visualizzazione predefinita e nella visualizzazione `simple`, mentre gli elementi `[size]` e `[capacity]` non vengono visualizzati nella visualizzazione `simple`.

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

Nella finestra **espressioni di controllo** usare l'identificatore di formato di **visualizzazione** per specificare una visualizzazione alternativa. La visualizzazione semplice viene visualizzata come **VEC, View (Simple)** :

![finestra Espressioni di controllo con visualizzazione semplice](../debugger/media/watch-simpleview.png "Finestra Espressioni di controllo con visualizzazione semplice")

## <a name="BKMK_Diagnosing_Natvis_errors"></a>Errori natvis

Quando il debugger rileva errori in una voce di visualizzazione, li ignora. Visualizza il tipo nel formato non elaborato o seleziona un'altra visualizzazione appropriata. È possibile usare la diagnostica natvis per comprendere il motivo per cui il debugger ha ignorato una voce di visualizzazione e per visualizzare la sintassi sottostante e gli errori di analisi.

**Per attivare la diagnostica natvis:**

- In **strumenti** > **Opzioni** (o **Opzioni** **debug** > ) > **debug** > **finestra di output**, impostare **i messaggi di diagnosticaC++ natvis (solo)** su **errore**, **avviso**o **dettagliato**, quindi selezionare **OK**.

Gli errori vengono visualizzati nella finestra **output** .

## <a name="BKMK_Syntax_reference"></a> Riferimento per la sintassi di Natvis

### <a name="BKMK_AutoVisualizer"></a> Elemento AutoVisualizer
L'elemento `AutoVisualizer` è il nodo radice del file *NATVIS* e contiene l'attributo `xmlns:` dello spazio dei nomi.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

L'elemento `AutoVisualizer` può includere elementi figlio [Type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)e [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="BKMK_Type"></a> Elemento Type

Un `Type` di base ha un aspetto simile a questo esempio:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 L'elemento `Type` specifica:

1. Tipo di visualizzazione da usare per l'attributo `Name`.

2. A quale valore di un oggetto di tale tipo deve essere simile (elemento `DisplayString` ).

3. Quali sono i membri del tipo quando l'utente espande il tipo in una finestra delle variabili (nodo `Expand`).

#### <a name="templated-classes"></a>Classi basate su modelli
L'attributo `Name` dell'elemento `Type` accetta un asterisco `*` come carattere jolly che può essere usato per i nomi di classi basate su modelli.

Nell'esempio seguente viene usata la stessa visualizzazione se l'oggetto è un `CAtlArray<int>` o `CAtlArray<float>`. Se è presente una voce di visualizzazione specifica per un `CAtlArray<float>`, avrà la precedenza rispetto a quella generica.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

È possibile fare riferimento ai parametri di modello nella voce di visualizzazione usando le macro $T 1, $T 2 e così via. Per esempi di queste macro, vedere i file *NATVIS* forniti con Visual Studio.

#### <a name="BKMK_Visualizer_type_matching"></a> Corrispondenza del tipo di visualizzatore
Se non è possibile convalidare una voce di visualizzazione, verrà usata la successiva visualizzazione disponibile.

#### <a name="inheritable-attribute"></a>Attributo Inheritable
L'attributo facoltativo `Inheritable` specifica se una visualizzazione si applica solo a un tipo di base o a un tipo di base e a tutti i tipi derivati. Il valore predefinito di `Inheritable` è `true`.

Nell'esempio seguente la visualizzazione si applica solo al tipo di `BaseClass`:

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Attributo Priority

L'attributo facoltativo `Priority` specifica l'ordine in cui utilizzare le definizioni alternative, se l'analisi di una definizione ha esito negativo. I valori possibili di `Priority` sono: `Low`, `MediumLow`,`Medium`, `MediumHigh`e `High`. Il valore predefinito è `Medium`. L'attributo `Priority` distingue solo tra le priorità incluse nello stesso file con *estensione natvis* .

Nell'esempio seguente viene prima di tutto analizzata la voce che corrisponde a 2015 STL. Se l'analisi non riesce, usa la voce alternativa per la versione 2013 di STL:

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
È possibile inserire un attributo `Optional` su qualsiasi nodo. Se una sottoespressione all'interno di un nodo facoltativo non viene analizzata, il debugger ignora tale nodo, ma applica le altre regole di `Type`. Nel tipo seguente `[State]` non è facoltativo, mentre `[Exception]` lo è.  Se `MyNamespace::MyClass` dispone di un campo denominato _`M_exceptionHolder`, verranno visualizzati sia il nodo `[State]` che il nodo `[Exception]`, ma se non è presente alcun campo `_M_exceptionHolder`, viene visualizzato solo il nodo `[State]`.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="BKMK_Condition_attribute"></a> Attributo Condition

L'attributo `Condition` facoltativo è disponibile per molti elementi di visualizzazione e specifica quando usare una regola di visualizzazione. Se l'espressione all'interno dell'attributo Condition viene risolta in `false`, la regola di visualizzazione non è applicabile. Se restituisce `true`o non esiste alcun attributo `Condition`, viene applicata la visualizzazione. È possibile usare questo attributo per la logica if-else nelle voci di visualizzazione.

La visualizzazione seguente, ad esempio, include due elementi `DisplayString` per un tipo di puntatore intelligente. Quando il membro `_Myptr` è vuoto, la condizione del primo elemento `DisplayString` viene risolta in `true`, in modo da visualizzare il form. Quando il membro `_Myptr` non è vuoto, la condizione restituisce `false`e viene visualizzato il secondo elemento `DisplayString`.

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

Gli attributi `IncludeView` e `ExcludeView` specificano gli elementi da visualizzare o non devono essere visualizzati in visualizzazioni specifiche. Nella specifica natvis seguente di `std::vector`, ad esempio, nella visualizzazione `simple` non vengono visualizzati gli elementi `[size]` e `[capacity]`.

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

È possibile utilizzare gli attributi `IncludeView` e `ExcludeView` sui tipi e sui singoli membri.

### <a name="BKMK_Versioning"></a> Elemento Version
L'elemento `Version` l'ambito di una voce di visualizzazione per un modulo e una versione specifici. L'elemento `Version` consente di evitare conflitti di nomi, ridurre le mancate corrispondenze involontarie e consente visualizzazioni diverse per diverse versioni del tipo.

Se un file di intestazione comune usato da moduli diversi definisce un tipo, la visualizzazione con versione viene visualizzata solo quando il tipo è nella versione del modulo specificata.

Nell'esempio seguente la visualizzazione è applicabile solo per il tipo di `DirectUI::Border` trovato nella `Windows.UI.Xaml.dll` dalla versione 1,0 alla 1,5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Non sono necessari sia `Min` che `Max`. Si tratta di attributi facoltativi. Non sono supportati caratteri jolly.

Il formato dell'attributo `Name` è *filename. ext*, ad esempio *Hello. exe* o *some. dll*. Non sono consentiti nomi di percorso.

### <a name="BKMK_DisplayString"></a>Elemento DisplayString
L'elemento `DisplayString` specifica una stringa da visualizzare come valore di una variabile. Accetta stringhe arbitrarie combinate con espressioni. Tutto ciò che è racchiuso tra parentesi graffe viene interpretato come un'espressione. Ad esempio, la voce di `DisplayString` seguente:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Indica che le variabili di tipo `CPoint` visualizzate come illustrato nella figura seguente:

 ![Usare un elemento DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Usare un elemento DisplayString")

Nell'espressione `DisplayString` `x` e `y`, che sono membri di `CPoint`, sono racchiusi tra parentesi graffe, pertanto i relativi valori vengono valutati. Nell'esempio viene inoltre illustrato come sfuggire a una parentesi graffa con parentesi graffe doppie (`{{` o `}}`).

> [!NOTE]
> L'elemento `DisplayString` è l'unico elemento che accetta stringhe arbitrarie e la sintassi con parentesi graffe. Tutti gli altri elementi di visualizzazione accettano solo le espressioni che possono essere valutate dal debugger.

### <a name="BKMK_StringView"></a>Elemento StringView

L'elemento `StringView` definisce un valore che il debugger può inviare al visualizzatore di testo incorporato. Ad esempio, data la seguente visualizzazione per il tipo di `ATL::CStringT`:

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

L'oggetto `CStringT` viene visualizzato in una finestra delle variabili come nell'esempio seguente:

![Elemento DisplayString CStringt](../debugger/media/dbg_natvis_displaystring_cstringt.png "Elemento DisplayString CStringT")

L'aggiunta di un elemento `StringView` indica al debugger che è possibile visualizzare il valore come visualizzazione di testo.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Durante il debug, è possibile selezionare l'icona della lente di ingrandimento accanto alla variabile, quindi selezionare **Visualizzatore di testo** per visualizzare la stringa a cui punta **m_pszData** .

 ![Dati CStringt con visualizzatore StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Dati CStringT con visualizzatore StringView")

L'espressione `{m_pszData,su}` include un C++ identificatore di formato **su**per visualizzare il valore come stringa Unicode. Per ulteriori informazioni, vedere [identificatori di formato C++in ](../debugger/format-specifiers-in-cpp.md).

### <a name="BKMK_Expand"></a>Espandi elemento

Il nodo `Expand` facoltativo Personalizza gli elementi figlio di un tipo visualizzato quando si espande il tipo in una finestra delle variabili. Il nodo `Expand` accetta un elenco di nodi figlio che definiscono gli elementi figlio.

- Se un nodo `Expand` non è specificato in una voce di visualizzazione, gli elementi figlio utilizzano le regole di espansione predefinite.

- Se un nodo `Expand` viene specificato senza nodi figlio, il tipo non è espandibile nelle finestre del debugger.

#### <a name="BKMK_Item_expansion"></a> Espansione di Item

 L'elemento `Item` è l'elemento più semplice e comune in un nodo `Expand`. `Item` definisce un singolo elemento figlio. Ad esempio, una classe `CRect` con i campi `top`, `left`, `right`e `bottom` presenta la seguente voce di visualizzazione:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Nella finestra del debugger, il tipo di `CRect` è simile a questo esempio:

![CRect con espansione elemento elemento](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect con espansione dell'elemento Item")

Il debugger valuta le espressioni specificate negli elementi `Width` e `Height` e Mostra i valori nella colonna **valore** della finestra delle variabili.

Il debugger crea automaticamente il nodo **[visualizzazione non elaborata]** per ogni espansione personalizzata. La schermata precedente Mostra il nodo **[RAW View]** espanso per mostrare come la visualizzazione non elaborata predefinita dell'oggetto è diversa dalla relativa visualizzazione natvis. L'espansione predefinita crea un sottoalbero per la classe base ed elenca tutti i membri dati della classe base come elementi figlio.

> [!NOTE]
> Se l'espressione dell'elemento Item punta a un tipo complesso, il nodo dell' **elemento** stesso è espandibile.

#### <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
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

![STD:: Vector con espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector con uso dell'espansione ArrayItems")

Il nodo `ArrayItems` deve avere:

- Un'espressione `Size` (che deve restituire un numero intero) per consentire al debugger di riconoscere la lunghezza della matrice.
- Espressione `ValuePointer` che punta al primo elemento (che deve essere un puntatore di un tipo di elemento che non è `void*`).

Il valore predefinito del limite inferiore della matrice è 0. Per eseguire l'override del valore, usare un elemento `LowerBound`. Di seguito sono riportati alcuni esempi di file con *estensione natvis* forniti con Visual Studio.

>[!NOTE]
>È possibile usare l'operatore `[]`, ad esempio `vector[i]`, con qualsiasi visualizzazione di matrice unidimensionale che usa `ArrayItems`, anche se il tipo stesso (ad esempio `CATLArray`) non consente questo operatore.

È anche possibile specificare matrici multidimensionali. In tal caso, per visualizzare correttamente gli elementi figlio, il debugger necessita di un numero leggermente maggiore di informazioni:

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

- `Direction` specifica se la matrice è in ordine di riga, principale o di colonna.
- `Rank` specifica l'ordine di priorità della matrice.
- L'elemento `Size` accetta il parametro `$i` implicito che sostituisce con l'indice delle dimensioni per individuare la lunghezza della matrice in quella dimensione. Nell'esempio precedente, l'espressione `_M_extent.M_base[0]` deve fornire la lunghezza della dimensione 0A, `_M_extent._M_base[1]` il primo e così via.

Ecco il modo in cui un oggetto `Concurrency::array` bidimensionale Cerca nella finestra del debugger:

![Matrice bidimensionale con espansione ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Matrice bidimensionale con espansione ArrayItems")

#### <a name="BKMK_IndexListItems_expansion"></a> Espansione di IndexListItems

È possibile utilizzare `ArrayItems` espansione solo se gli elementi della matrice sono disposti in modo contiguo nella memoria. Il debugger raggiunge l'elemento successivo semplicemente incrementando il relativo puntatore. Se è necessario modificare l'indice nel nodo valore, utilizzare `IndexListItems` nodi. Ecco una visualizzazione con un nodo `IndexListItems`:

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

L'unica differenza tra `ArrayItems` e `IndexListItems` è la `ValueNode`, che prevede l'espressione completa per l'elemento i<sup>th</sup> con il parametro di `$i` implicito.

>[!NOTE]
>È possibile usare l'operatore `[]`, ad esempio `vector[i]`, con qualsiasi visualizzazione di matrice unidimensionale che usa `IndexListItems`, anche se il tipo stesso (ad esempio `CATLArray`) non consente questo operatore.

#### <a name="BKMK_LinkedListItems_expansion"></a> Espansione di LinkedListItems

Se il tipo visualizzato rappresenta un elenco collegato, il debugger può visualizzarne i figli tramite un nodo `LinkedListItems` . La visualizzazione seguente per il tipo di `CAtlList` utilizza `LinkedListItems`:

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

Il debugger valuta le espressioni `NextPointer` e `ValueNode` nel contesto dell'elemento `LinkedListItems` node, non del tipo di elenco padre. Nell'esempio precedente, `CAtlList` dispone di una classe `CNode` (presente in `atlcoll.h`) che rappresenta un nodo dell'elenco collegato. `m_pNext` e `m_element` sono campi di tale classe `CNode`, non della classe `CAtlList`.

`ValueNode` possono essere lasciati vuoti o usare `this` per fare riferimento al nodo `LinkedListItems` stesso.

#### <a name="customlistitems-expansion"></a>Espansione CustomListItems
L'espansione `CustomListItems` consente di scrivere una logica personalizzata per attraversare una struttura dei dati, ad esempio una tabella hash. Usare `CustomListItems` per visualizzare le strutture dei dati in grado C++ di usare espressioni per tutti gli elementi necessari per la valutazione, ma non è sufficiente adattare lo stamp per `ArrayItems`, `IndexListItems`o `LinkedListItems`.

Il Visualizzatore seguente per `CAtlMap` è un ottimo esempio in cui `CustomListItems` è appropriato.

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

È possibile usare `Exec` per eseguire codice all'interno di un'espansione `CustomListItems`, usando le variabili e gli oggetti definiti nell'espansione. È possibile utilizzare gli operatori logici, gli operatori aritmetici e gli operatori di assegnazione con `Exec`. Non è possibile usare `Exec` per valutare le funzioni.

`CustomListItems` supporta le funzioni intrinseche seguenti:

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

#### <a name="BKMK_TreeItems_expansion"></a> Espansione di TreeItems
 Se il tipo visualizzato rappresenta un albero, il debugger può esaminare l'albero e visualizzarne i figli tramite un nodo `TreeItems` . Di seguito è illustrata la visualizzazione per il tipo di `std::map` usando un nodo `TreeItems`:

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

La sintassi è simile al nodo `LinkedListItems`. `LeftPointer`, `RightPointer`e `ValueNode` vengono valutati nel contesto della classe del nodo della struttura ad albero. `ValueNode` possono essere lasciati vuoti o usare `this` per fare riferimento al nodo `TreeItems` stesso.

#### <a name="BKMK_ExpandedItem_expansion"></a> Espansione di ExpandedItem
 L'elemento `ExpandedItem` genera una visualizzazione figlio aggregata visualizzando le proprietà delle classi base o dei membri dati come se fossero figli del tipo visualizzato. Il debugger valuta l'espressione specificata e accoda i nodi figlio del risultato all'elenco figlio del tipo visualizzato.

Ad esempio, il tipo di puntatore intelligente `auto_ptr<vector<int>>` in genere viene visualizzato come:

 ![espansione&#95;predefinita&#60;del&#60;vettore&#62; &#62; di tipo auto PTR](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Espansione predefinita")

 Per visualizzare i valori del vettore, è necessario eseguire il drill-down di due livelli nella finestra delle variabili, passando il membro `_Myptr`. Aggiungendo un elemento `ExpandedItem`, è possibile eliminare la variabile `_Myptr` dalla gerarchia e visualizzare direttamente gli elementi del vettore:

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![espansione&#95;auto&#60;PTR&#60;vector&#62; &#62; int ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Espansione di ExpandedItem")

Nell'esempio seguente viene illustrato come aggregare proprietà dalla classe base in una classe derivata. Si supponga che la classe `CPanel` derivi da `CFrameworkElement`. Invece di ripetere le proprietà che provengono dalla classe `CFrameworkElement` di base, la visualizzazione del nodo `ExpandedItem` Accoda tali proprietà all'elenco figlio della classe `CPanel`.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

In questo caso è necessario l'identificatore di formato **nd** che disattiva la corrispondenza della visualizzazione per la classe derivata. In caso contrario, l'espressione `*(CFrameworkElement*)this` provocherebbe nuovamente l'applicazione della visualizzazione `CPanel`, perché le regole di corrispondenza del tipo di visualizzazione predefinite lo considerano quello più appropriato. Usare l'identificatore di formato **ND** per indicare al debugger di usare la visualizzazione della classe base o l'espansione predefinita se la classe base non ha alcuna visualizzazione.

#### <a name="BKMK_Synthetic_Item_expansion"></a> Espansione di elementi Synthetic
 Il nodo `ExpandedItem` esegue la funzione opposta rispetto all'elemento `Synthetic`, che fornisce una visualizzazione dei dati più semplice eliminando le gerarchie. Consente di creare un elemento figlio artificiale che non è il risultato di un'espressione. L'elemento Artificial può avere elementi figlio propri. Nell'esempio seguente nella visualizzazione del tipo `Concurrency::array` viene usato un nodo `Synthetic` per mostrare un messaggio di diagnostica all'utente:

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

 ![Concurrency:: array con espansione di elementi sintetici](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrency:: array con espansione di elementi sintetici")

### <a name="BKMK_HResult"></a>HResult (elemento)
 L'elemento `HResult` consente di personalizzare le informazioni visualizzate per un **HRESULT** nelle finestre del debugger. L'elemento `HRValue` deve contenere il valore a 32 bit di **HRESULT** da personalizzare. L'elemento `HRDescription` contiene le informazioni da visualizzare nella finestra del debugger.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="BKMK_UIVisualizer"></a>Elemento UIVisualizer
Un elemento `UIVisualizer` consente di registrare un plug-in del visualizzatore grafico con il debugger. Un visualizzatore grafico crea una finestra di dialogo o un'altra interfaccia che mostra una variabile o un oggetto in modo coerente con il relativo tipo di dati. Il plug-in del visualizzatore deve essere creato come [VSPackage](../extensibility/internals/vspackages.md)e deve esporre un servizio che può essere utilizzato dal debugger. Il file *. natvis* contiene le informazioni di registrazione per il plug-in, ad esempio il nome, il GUID del servizio esposto e i tipi che è in grado di visualizzare.

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

- Una coppia `ServiceId` - `Id` attributo identifica un `UIVisualizer`. Il `ServiceId` è il GUID del servizio esposto dal pacchetto del visualizzatore. `Id` è un identificatore univoco che distingue i visualizzatori, se un servizio ne fornisce più di uno. Nell'esempio precedente, lo stesso servizio del visualizzatore fornisce due visualizzatori.

- L'attributo `MenuName` definisce il nome di un visualizzatore da visualizzare nell'elenco a discesa accanto all'icona della lente di ingrandimento nel debugger. Ad esempio,

  ![Menu di scelta rapida del menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu di scelta rapida UIVisualizer")

Ogni tipo definito nel file *natvis* deve elencare in modo esplicito tutti i visualizzatori dell'interfaccia utente in grado di visualizzarli. Il debugger corrisponde ai riferimenti del visualizzatore nelle voci di tipo con i visualizzatori registrati. Ad esempio, la voce di tipo seguente per `std::vector` fa riferimento al `UIVisualizer` nell'esempio precedente.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 È possibile vedere un esempio di `UIVisualizer` nell'estensione [Image Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) utilizzata per visualizzare le bitmap in memoria.

### <a name="BKMK_CustomVisualizer"></a>Elemento CustomVisualizer
 `CustomVisualizer` è un punto di estendibilità che specifica un'estensione VSIX che è possibile scrivere per controllare le visualizzazioni in Visual Studio Code. Per ulteriori informazioni sulla scrittura di estensioni VSIX, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

È molto più lavoro scrivere un visualizzatore personalizzato rispetto a una definizione natvis XML, ma non sono disponibili vincoli sui vincoli che natvis o non supporta. I visualizzatori personalizzati hanno accesso al set completo di API di estendibilità del debugger, che possono eseguire query e modificare il processo del debug o comunicare con altre parti di Visual Studio.

 È possibile utilizzare gli attributi `Condition`, `IncludeView`e `ExcludeView` negli elementi `CustomVisualizer`.

 ## <a name="limitations"></a>Limitazioni

Le personalizzazioni di natvis funzionano con classi e struct, ma non con typedef.

Natvis non supporta i visualizzatori per i tipi primitivi (ad esempio `int`, `bool`) o per i puntatori ai tipi primitivi. In questo scenario, un'opzione consiste nell'usare l' [identificatore di formato](../debugger/format-specifiers-in-cpp.md) appropriato per il caso d'uso. Se ad esempio si usa `double* mydoublearray` nel codice, è possibile usare un identificatore di formato di matrice nella finestra **espressioni di controllo** del debugger, ad esempio l'espressione `mydoublearray, [100]`, che mostra i primi 100 elementi.