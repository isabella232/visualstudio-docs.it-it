---
title: Convenzioni di denominazione .NET per i file EditorConfig
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 644c73dea58936773acde98ccc535dfc61979288
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251698"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Convenzioni di denominazione .NET per EditorConfig

Le convenzioni di denominazione riguardano la denominazione degli elementi di codice, ad esempio classi, proprietà e metodi. Ad esempio, è possibile specificare che i metodi pubblici devono essere scritti in lettere maiuscole o che i metodi asincroni devono terminare con "Async". È anche possibile applicare queste regole specificandole in un [file EDITORCONFIG](../ide/create-portable-custom-editor-options.md). Le violazioni delle regole di denominazione vengono visualizzate nell'**Elenco errori** o come suggerimento sotto il nome, a seconda della gravità scelta per la regola. Non è necessario compilare il progetto per visualizzare le violazioni.

Per ogni convenzione di denominazione, è necessario specificare i simboli a cui viene applicata, uno stile di denominazione e un livello di gravità per l'applicazione della convenzione, usando le proprietà descritte di seguito. L'ordine delle proprietà non è importante.

Per iniziare, scegliere un titolo per la regola di denominazione da usare in ognuna delle proprietà necessarie per descrivere la regola in modo completo. Ad esempio, `public_members_must_be_capitalized` è un buon nome descrittivo per una regola di denominazione. Questa pagina farà riferimento al titolo scelto come a **<namingRuleTitle\>** nelle sezioni che seguono.

## <a name="symbols"></a>Simboli

Per prima cosa, identificare un gruppo di simboli a cui applicare la regola di denominazione. Questa proprietà ha il formato seguente:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Assegnare un nome al gruppo di simboli sostituendo il valore **< symbolTitle\>** con un titolo descrittivo, ad esempio `public_symbols`. Si userà il valore **< symbolTitle\>** nei tre nomi di proprietà che indicano a quali simboli la regola viene applicata (tipi di simboli, livelli di accessibilità e modificatori).

### <a name="kinds-of-symbols"></a>Tipi di simboli

Per descrivere il tipo di simboli a cui applicare la regola di denominazione, specificare una proprietà nel formato seguente:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

L'elenco seguente riporta i valori consentiti ed è possibile specificare più valori separandoli con una virgola.

- \* (usare questo valore per specificare tutti i simboli)
- namespace
- classe
- struct
- interfaccia
- enum
- proprietà
- metodo
- campo
- event
- delegato
- parametro
- type_parameter
- locali
- local_function

### <a name="accessibility-levels-of-symbols"></a>Livelli di accessibilità dei simboli

Per descrivere i livelli di accessibilità dei simboli a cui si vuole applicare la regola di denominazione, specificare un nome di proprietà nel formato seguente:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

L'elenco seguente riporta i valori consentiti ed è possibile specificare più valori separandoli con una virgola.

- \* (usare questo valore per specificare tutti i livelli di accessibilità)
- public
- internal o friend
- private
- protected
- protected\_internal o protected_friend
- private\_protected
- locali

   Il livello di accessibilità `local` si applica ai simboli definiti all'interno di un metodo. È utile per la definizione delle convenzioni di denominazione per i simboli la cui accessibilità non può essere specificata nel codice. Ad esempio, se si specifica `applicable_accessibilities = local` per una convenzione di denominazione per le costanti (`required_modifiers = const`), la regola viene applicata solo alle costanti definite all'interno di un metodo e non a quelle definite in un tipo.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Modificatori dei simboli (facoltativi)

Per descrivere i modificatori dei simboli a cui si vuole applicare la regola di denominazione, specificare un nome di proprietà nel formato seguente:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

L'elenco seguente mostra i valori consentiti. Se si specificano più valori, separarli con virgole:

- `abstract` o `must_inherit`
- `async`
- `const`
- `readonly`
- `static` o `shared`

   > [!NOTE]
   > Se è presente una regola di denominazione per i simboli `static` o `shared`, la regola viene applicata anche ai simboli `const` perché sono statici in modo implicito. Se non si vuole che la regola di denominazione `static` venga applicata ai simboli `const`, creare una regola di denominazione separata per i simboli `const`.

Una regola di denominazione cerca le firme corrispondenti con *tutti* i modificatori specificati in `required_modifiers`. Se si omette questa proprietà, viene usato il valore predefinito di un elenco vuoto, ovvero non viene richiesto alcun modificatore specifico per trovare una corrispondenza. Ciò significa che i modificatori di un simbolo non hanno alcun effetto sull'applicazione di questa regola.

> [!TIP]
> Non specificare un valore `*` per `required_modifiers`. Omettere semplicemente la proprietà `required_modifiers` e la regola di denominazione verrà applicata a qualsiasi tipo di modificatore.

## <a name="style"></a>Stile

Ora che è stato identificato il gruppo di simboli a cui applicare la regola di denominazione, è possibile descrivere lo stile di denominazione. Uno stile può stabilire che il nome abbia un determinato prefisso o suffisso o che le singole parole nel nome siano separate da un determinato carattere. È anche possibile specificare uno stile per l'uso di maiuscole e minuscole. La proprietà dello stile ha il formato seguente:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Assegnare un nome allo stile sostituendo il valore **< styleTitle\>** con un titolo descrittivo, ad esempio `first_word_upper_case_style`. Si userà il valore **< styleTitle\>** nei nomi di proprietà che descrivono lo stile di denominazione (prefisso, suffisso, carattere separatore delle parole e lettere maiuscole e minuscole). Usare una o più di queste proprietà per descrivere il proprio stile.

### <a name="require-a-prefix"></a>Richiedere un prefisso

Per specificare che i nomi dei simboli devono iniziare con determinati caratteri, usare questa proprietà:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Richiedere un suffisso

Per specificare che i nomi dei simboli devono terminare con determinati caratteri, usare questa proprietà:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Richiedere un determinato separatore delle parole

Per specificare che le singole parole nei nomi dei simboli devono essere separate da un determinato carattere, usare questa proprietà:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Richiedere uno stile per maiuscole e minuscole

Per specificare uno stile particolare per l'uso di maiuscole e minuscole nei nomi dei simboli, usare questa proprietà:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

I valori consentiti per questa proprietà sono:

- pascal_case
- camel_case
- first\_word_upper
- all\_upper
- all_lower

> [!NOTE]
> Nell'ambito dello stile di denominazione è necessario specificare uno stile per le lettere maiuscole e minuscole. In caso contrario, lo stile di denominazione potrebbe essere ignorato.

## <a name="severity"></a>Gravità

Per descrivere la gravità di una violazione della regola di denominazione, specificare una proprietà nel formato seguente:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

Nella tabella seguente sono riportati i valori consentiti per la gravità, con il relativo significato:

Gravità | Effetto
------------ | -------------
none | La regola viene eliminata completamente.
refactoring o silent | Se questo stile non viene rispettato, non viene visualizzato alcun avviso all'utente, ma il codice generato automaticamente segue comunque questo stile.
suggestion | Se questo stile non viene rispettato, viene visualizzato un suggerimento per l'utente, indicato dai primi due caratteri sottolineati con dei puntini. Non ha alcun effetto in fase di compilazione.
warning | Se questo stile non viene rispettato, viene visualizzato un avviso del compilatore nell'**Elenco errori**.
error | Se questo stile non viene rispettato, viene visualizzato un errore del compilatore nell'**Elenco errori**.

> [!NOTE]
> Non è necessario compilare il progetto per visualizzare le violazioni delle regole di denominazione. Vengono visualizzate quando il codice viene modificato, nell'**Elenco errori** o come suggerimento.

## <a name="rule-order"></a>Ordine delle regole

::: moniker range="vs-2017"

Le convenzioni di denominazione devono essere ordinate dalla convenzione più specifica a quella meno specifica nel file EditorConfig. La prima regola rilevata che può essere applicata è l'unica regola che viene applicata. Se tuttavia sono presenti più *proprietà* della regola con lo stesso nome, la proprietà con tale nome individuata più di recente ha la precedenza. Per altre informazioni, vedere [Gerarchia e precedenza dei file](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

A partire da Visual Studio 2019 versione 16.2, l'ordine in base al quale sono definite le regole di denominazione in un file EditorConfig non è rilevante. Visual Studio ordina infatti automaticamente le regole di denominazione in base alla definizione delle regole stesse. L' [estensione del servizio di linguaggio EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) può analizzare un file EditorConfig e segnalare i casi in cui l'ordinamento delle regole nel file è diverso da quello che verrà utilizzato dal compilatore in fase di esecuzione.

Se si usa una versione precedente di Visual Studio, le convenzioni di denominazione devono essere ordinate dalla più specifica alla meno specifica nel file EditorConfig. La prima regola rilevata che può essere applicata è l'unica regola che viene applicata. Se tuttavia sono presenti più *proprietà* della regola con lo stesso nome, la proprietà con tale nome individuata più di recente ha la precedenza. Per altre informazioni, vedere [Gerarchia e precedenza dei file](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Stili di denominazione predefiniti

Se non si specificano regole di denominazione personalizzate, Visual Studio usa gli stili predefiniti seguenti:

- Per classi, struct, enumerazioni, proprietà ed eventi con accessibilità `public`, `private`, `internal`, `protected` o `protected_internal`, lo stile di denominazione predefinito è basato sulla convenzione Pascal.

- Per le interfacce con accessibilità `public`, `private`, `internal`, `protected` o `protected_internal`, lo stile di denominazione predefinito è basato sulla convenzione Pascal con il prefisso obbligatorio **I**.

## <a name="example"></a>Esempio

Il seguente file con estensione *editorconfig* contiene una convenzione di denominazione che specifica che i nomi di proprietà, metodi, campi, eventi e delegati pubblici devono avere la prima lettera maiuscola. Si noti che questa convenzione di denominazione specifica più tipi di simboli a cui applicare la regola, usando una virgola per separare i valori.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

La schermata seguente illustra l'effetto di questa convenzione di denominazione nell'editor. I nomi di due variabili pubbliche non hanno la prima lettera maiuscola. Una è `const` e una è `readonly`. Poiché la regola di denominazione si applica solo ai simboli `readonly`, solo la variabile `readonly` indica un suggerimento della regola di denominazione.

![Suggerimento della regola di denominazione](media/editorconfig-naming-rule-suggestion.png)

Ora si modifica la gravità della violazione, che diventa `warning`:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Se si chiude e si riapre il file di codice, anziché il suggerimento sotto la violazione del nome, si visualizzano una linea verde ondulata e un avviso nell'**Elenco errori**:

![Avviso della regola di denominazione](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Vedere anche

- [Convenzioni del linguaggio](editorconfig-language-conventions.md)
- [Convenzioni di formattazione](editorconfig-formatting-conventions.md)
- [Convenzioni di denominazione Roslyn](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Creare impostazioni personalizzate e portabili per l'editor](../ide/create-portable-custom-editor-options.md)
- [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](editorconfig-code-style-settings-reference.md)
