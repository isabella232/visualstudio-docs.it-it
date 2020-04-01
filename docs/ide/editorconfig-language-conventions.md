---
title: Convenzioni del linguaggio .NET per EditorConfig
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0c06d6c16082a8300092e36b9bbed126c66f8af4
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80528023"
---
# <a name="language-conventions"></a>Convenzioni del linguaggio

Le convenzioni del linguaggio per EditorConfig in Visual Studio rientrano in due categorie: quelle che si applicano a Visual Basic e C# e quelle specifiche di C#. Le convenzioni del linguaggio influiscono sul modo in cui vengono usati vari aspetti di un linguaggio di programmazione, ad esempio modificatori e parentesi.

> [!TIP]
> - Per vedere gli esempi di codice nel linguaggio di programmazione preferito, selezionarlo tramite lo strumento di selezione del linguaggio nell'angolo in alto a destra della finestra del browser.
>
>   ![Controllo di selezione del linguaggio di codice](media/code-language-picker.png)
>
> - Usare i collegamenti disponibili **in questo articolo** per passare alle diverse sezioni della pagina.

## <a name="rule-format"></a>Formato delle regole

Le regole per le convenzioni del linguaggio hanno il formato generale seguente:

`option_name = value:severity`

Per ogni convenzione del linguaggio, si specifica un valore che definisce se o quando preferire lo stile. Molte regole accettano `true` un valore di `false` (preferire questo stile) o (non preferiscono questo stile). Altre regole accettano `when_on_single_line` `never`valori quali o . La seconda parte della regola specifica la [gravità](#severity-levels).

::: moniker range=">=vs-2019"

> [!NOTE]
> Poiché le convenzioni del linguaggio vengono applicate dagli analizzatori, è anche possibile impostarne la gravità utilizzando la sintassi di configurazione predefinita per gli analizzatori. La sintassi `dotnet_diagnostic.<rule ID>.severity = <severity>`assume il `dotnet_diagnostic.IDE0040.severity = silent`formato , ad esempio , . Per ulteriori informazioni, consultate Impostare la [gravità della regola in un file EditorConfig.](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)

::: moniker-end

## <a name="severity-levels"></a>Livelli di gravità

La gravità di una convenzione del linguaggio specifica il livello in cui applicare lo stile selezionato. Nella tabella seguente sono elencati i valori di gravità possibili e i relativi effetti:

Gravità | Effetto
:------- | ------
`error` | Quando questa regola di stile viene violata, viene visualizzato un errore del compilatore.
`warning` | Quando questa regola di stile viene violata, viene visualizzato un avviso del compilatore.
`suggestion` | Quando questa regola di stile viene violata, viene visualizzato un suggerimento all'utente. I suggerimenti sono indicati da tre punti grigi sotto i primi due caratteri.
`silent` | Quando questa regola viene violata non viene visualizzato alcun avviso all'utente. Le funzionalità di generazione del codice generano tuttavia il codice in questo stile. Le `silent` regole con gravità partecipano alla pulizia e vengono visualizzate nel menu **Azioni rapide e refactoring.**
`none` | Quando questa regola viene violata non viene visualizzato alcun avviso all'utente. Le funzionalità di generazione del codice generano tuttavia il codice in questo stile. Le regole con gravità `none` non vengono mai visualizzate nel menu **Azioni rapide e refactoring**. Nella maggior parte dei casi sono considerate "disabilitate" o "ignorate".

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Configurare automaticamente gli stili di codice

A partire da Visual Studio 2019 versione 16.3, è possibile configurare le regole di stile del codice dal menu lampadina [Azioni rapide](quick-actions.md) dopo che si verifica una violazione di stile.

Per modificare la convenzione di stile del codice:

1. Posizionare il puntatore del mouse sulla scheda ondulata nell'editor, quindi aprire il menu della lampadina visualizzato. Scegliere **Configura o Elimina problemi** > **Configurare \<l'ID regola> lo stile**del codice .

   ![Configurare lo stile del codice dal menu lampadina in Visual StudioConfigure code style from light bulb menu in Visual Studio](media/vs-2019/configure-code-style.png)

2. Da lì, scegliere una delle opzioni di stile del codice.

   ![Configurare l'impostazione dello stile del codice](media/vs-2019/configure-code-style-setting.png)

   Visual Studio aggiunge o modifica l'impostazione di configurazione nel file EditorConfig, come illustrato nella casella di anteprima.

Per modificare la gravità della violazione dello stile del codice, seguire la stessa procedura, ma scegliere **Configura \<ID regola> gravità** anziché **Configura \<ID regola> stile codice**. Per ulteriori informazioni, vedere [Configurare automaticamente](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity)la gravità della regola .

::: moniker-end

## <a name="net-code-style-settings"></a>Impostazioni di stile del codice .NET

Le regole di stile illustrate in questa sezione sono applicabili a C# e Visual Basic.

- [Qualificatori "This." e "Me."](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [Parole chiave del linguaggio anziché nomi di tipi di framework per i riferimenti ai tipiLanguage keywords instead of framework type names for type references](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - dotnet\_style\_predefined\_type\_for\_member_access
- [Preferenze modificatore](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - visual\_basic\_preferred\_modifier_order
  - dotnet\_style\_readonly\_field
- [Preferenze per parentesi](#parentheses-preferences)
  - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_operators
  - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [Preferenze a livello di espressione](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - dotnet\_style\_explicit\_tuple_names
  - dotnet\_style\_prefer\_inferred\_tuple_names
  - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
  - dotnet\_style\_prefer\_auto\_properties
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method
  - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
  - dotnet\_style\_prefer\_compound\_assignment
- [Preferenze di controllo "Null"](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>"Questo." e "Me"

È possibile applicare questa regola di stile a campi, proprietà, metodi o eventi. Il valore **true** indica la preferenza a far precedere il simbolo del codice da `this.` in C# o da `Me.` in Visual Basic. Il valore **false** indica la preferenza a _non_ far precedere l'elemento di codice da `this.` o da `Me.`.

Queste regole possono essere visualizzate in un file *.editorconfig* come indicato di seguito:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Nome regola** | dotnet_style_qualification_for_field |
| **ID regola** | IDE0003 e IDE0009 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza a far precedere i campi da `this.` in C# o da `Me.` in Visual Basic<br /><br />`false` - Indica la preferenza a _non_ far precedere i campi da `this.` o da `Me.` |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Nome regola** | dotnet_style_qualification_for_property |
| **ID regola** | IDE0003 e IDE0009 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza a far precedere le proprietà da `this.` in C# o da `Me.` in Visual Basic<br /><br />`false` - Indica la preferenza a _non_ far precedere le proprietà da `this.` o da `Me.` |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Nome regola** | dotnet_style_qualification_for_method |
| **ID regola** | IDE0003 e IDE0009 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza a far precedere i metodi da `this.` in C# o da `Me.` in Visual Basic.<br /><br />`false` - Indica la preferenza a _non_ far precedere i metodi da `this.` o da `Me.`. |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Nome regola** | dotnet_style_qualification_for_event |
| **ID regola** | IDE0003 e IDE0009 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza a far precedere gli eventi da `this.` in C# o da `Me.` in Visual Basic.<br /><br />`false` - Indica la preferenza a _non_ far precedere gli eventi da `this.` o da `Me.`. |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>Parole chiave del linguaggio anziché nomi dei tipi di framework per i riferimenti ai tipi

È possibile applicare questa regola di stile a variabili locali, parametri dei metodi e membri delle classi oppure come regola separata alle espressioni di accesso ai membri di tipo. Il valore **true** indica la preferenza per la parola chiave del linguaggio (ad esempio, `int` o `Integer`) anziché per il nome del tipo (ad esempio, `Int32`) per i tipi con una parola chiave che li rappresenta. Il valore **false** indica la preferenza per il nome del tipo rispetto alla parola chiave del linguaggio.

Queste regole possono essere visualizzate in un file *.editorconfig* come indicato di seguito:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Nome regola** | dotnet_style_predefined_type_for_locals_parameters_members |
| **ID regola** | IDE0012 e IDE0014 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per la parola chiave del linguaggio per variabili locali, parametri dei metodi e membri delle classi rispetto al nome del tipo per i tipi con una parola chiave che li rappresenta<br /><br />`false` - Indica la preferenza per il nome del tipo per variabili locali, parametri dei metodi e membri delle classi rispetto alla parola chiave del linguaggio |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

#### <a name="dotnet_style_predefined_type_for_member_access"></a>dotnet\_style\_predefined\_type\_for\_member_access

|||
|-|-|
| **Nome regola** | dotnet_style_predefined_type_for_member_access |
| **ID regola** | IDE0013 e IDE0015 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per la parola chiave del linguaggio per le espressioni di accesso ai membri rispetto al nome del tipo per i tipi con una parola chiave che li rappresenta<br /><br />`false` - Indica la preferenza per il nome del tipo per le espressioni di accesso ai membri rispetto alla parola chiave del linguaggio |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

### <a name="modifier-preferences"></a><a name="normalize-modifiers"></a>Preferenze del modificatore

Le regole di stile in questa sezione riguardano le preferenze del modificatore, inclusa la richiesta di modificatori dell'accessibilità, la specifica dell'ordinamento preferito dei modificatori e il modificatore di sola lettura.

Queste regole possono essere visualizzate in un file *.editorconfig* come indicato di seguito:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Nome regola** | dotnet_style_require_accessibility_modifiers |
| **ID regola** | IDE0040 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `always` - Indica la preferenza che i modificatori dell'accessibilità vengano specificati.<br /><br />`for_non_interface_members` - Indica la preferenza che i modificatori dell'accessibilità vengano dichiarati, fatta eccezione per i membri dell'interfaccia pubblica. È lo stesso di **always** ed è stato aggiunto per correzioni future se C# aggiunge metodi di interfaccia predefiniti.<br /><br />`never` - Non indica la preferenza che i modificatori dell'accessibilità vengano specificati.<br /><br />`omit_if_default` - Indica la preferenza che i modificatori dell'accessibilità vengano specificati, a meno che non siano il modificatore predefinito. |
| **Impostazione predefinita di Visual Studio** | `for_non_interface_members:silent` |
| **Versione introdotta** | Visual Studio 2017 versione 15.5 |

Esempi di codice:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Nome regola** | csharp_preferred_modifier_order |
| **ID regola** | IDE0036 |
| **Lingue applicabili** | C# |
| **Valori** | Uno o più modificatori C#, come `public`, `private` e `protected` |
| **Impostazione predefinita di Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Versione introdotta** | Visual Studio 2017 versione 15.5 |

- Quando questa regola è impostata su un elenco di modificatori, p l'ordinamento specificato.
- Quando questa regola viene omessa dal file, non preferisce un ordine di modificatori.

Esempi di codice:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Nome regola** | visual_basic_preferred_modifier_order |
| **ID regola** | IDE0036 |
| **Lingue applicabili** | Visual Basic |
| **Valori** | Uno o più modificatori Visual Basic, come `Partial`, `Private` e `Public` |
| **Impostazione predefinita di Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Versione introdotta** | Visual Studio 2017 versione 15.5 |

- Quando questa regola è impostata su un elenco di modificatori, p l'ordinamento specificato.
- Quando questa regola viene omessa dal file, non preferisce un ordine di modificatori.

Esempi di codice:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|||
|-|-|
| **Nome regola** | visual_basic_style_unused_value_expression_statement_preference |
| **ID regola** | IDE0058 |
| **Lingue applicabili** | Visual Basic |
| **Valori** | `unused_local_variable:silent` |
| **Impostazione predefinita di Visual Studio** | `unused_local_variable:silent` |

Esempi di codice:

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|||
|-|-|
| **Nome regola** | visual_basic_style_unused_value_assignment_preference |
| **ID regola** | IDE0059 |
| **Lingue applicabili** | Visual Basic |
| **Valori** | `unused_local_variable:silent` |
| **Impostazione predefinita di Visual Studio** | `unused_local_variable:silent` |

Esempi di codice:

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Nome regola** | dotnet_style_readonly_field |
| **ID regola** | IDE0044 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza a contrassegnare i campi con `readonly` (C#) o `ReadOnly` (Visual Basic) se vengono assegnati solo inline o all'interno di un costruttore<br /><br />`false` - Non specifica alcuna preferenza tra `readonly` (C#) e `ReadOnly` (Visual Basic) per contrassegnare i campi |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |

Esempi di codice:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

### <a name="parentheses-preferences"></a>Preferenze per parentesi

Le regole di stile in questa sezione riguardano le preferenze per parentesi, incluso l'uso di parentesi per operatori aritmetici, relazionali e altri operatori binari.

Queste regole possono essere visualizzate in un file *.editorconfig* come indicato di seguito:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|||
|-|-|
| **Nome regola** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **ID regola** | IDE0047 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `always_for_clarity` - Indica la preferenza per le parentesi per chiarire la precedenza dell'operatore aritmetico (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`)<br /><br />`never_if_unnecessary` - Indica la preferenza a non avere alcuna parentesi quando la precedenza dell'operatore aritmetico (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) è ovvia |
| **Impostazione predefinita di Visual Studio** | `always_for_clarity:silent` |
| **Versione introdotta** | Visual Studio 2017 versione 15.8 |

Esempi di codice:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|||
|-|-|
| **Nome regola** | dotnet_style_parentheses_in_relational_binary_operators |
| **ID regola** | IDE0047 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `always_for_clarity` - Indica la preferenza per le parentesi per chiarire la precedenza dell'operatore relazionale (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`)<br /><br />`never_if_unnecessary` - Indica la preferenza a non avere alcuna parentesi quando la precedenza dell'operatore relazionale (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) è ovvia |
| **Impostazione predefinita di Visual Studio** | `always_for_clarity:silent` |
| **Versione introdotta** | Visual Studio 2017 versione 15.8 |

Esempi di codice:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|||
|-|-|
| **Nome regola** | dotnet_style_parentheses_in_other_binary_operators |
| **ID regola** | IDE0047 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `always_for_clarity` - Indica la preferenza per le parentesi per chiarire la precedenza dell'altro operatore binario (`&&`, `||`, `??`)<br /><br />`never_if_unnecessary` - Indica la preferenza a non avere alcuna parentesi quando la precedenza dell'altro operatore binario (`&&`, `||`, `??`) è ovvia |
| **Impostazione predefinita di Visual Studio** | `always_for_clarity:silent` |
| **Versione introdotta** | Visual Studio 2017 versione 15.8 |

Esempi di codice:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Nome regola** | dotnet_style_parentheses_in_other_operators |
| **ID regola** | IDE0047 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `always_for_clarity` - Indica la preferenza per le parentesi per chiarire la precedenza dell'operatore<br /><br />`never_if_unnecessary` - Indica la preferenza a non avere alcuna parentesi quando la precedenza dell'operatore è ovvia |
| **Impostazione predefinita di Visual Studio** | `never_if_unnecessary:silent` |
| **Versione introdotta** | Visual Studio 2017 versione 15.8 |

Esempi di codice:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>Preferenze a livello di espressione

Le regole di stile in questa sezione riguardano preferenze a livello di espressione, incluso l'uso di inizializzatori di oggetto, inizializzatori di raccolta, nomi di tupla espliciti o dedotti e tipi anonimi dedotti.

Queste regole possono essere visualizzate in un file *.editorconfig* come indicato di seguito:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Nome regola** | dotnet_style_object_initializer |
| **ID regola** | IDE0017 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza a inizializzare gli oggetti usando gli inizializzatori di oggetto, laddove possibile<br /><br />`false` - Indica la preferenza a *non* inizializzare gli oggetti usando gli inizializzatori di oggetto |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Nome regola** | dotnet_style_collection_initializer |
| **ID regola** | IDE0028 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza a inizializzare le raccolte usando gli inizializzatori di insieme, laddove possibile<br /><br />`false` - Indica la preferenza a *non* inizializzare le raccolte usando gli inizializzatori di insieme |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_style\_explicit\_tuple_names

|||
|-|-|
| **Nome regola** | dotnet_style_explicit_tuple_names |
| **ID regola** | IDE0033 |
| **Lingue applicabili** | C# 7.0+ e Visual Basic 15+ |
| **Valori** | `true` - Indica la preferenza per i nomi di tupla rispetto alle proprietà ItemX<br /><br />`false` - Indica la preferenza per le proprietà ItemX rispetto ai nomi di tupla |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_inferred_tuple_names |
| **ID regola** | IDE0037 |
| **Lingue applicabili** | C# 7.1+ e Visual Basic 15+ |
| **Valori** | `true` - Indica la preferenza per i nomi di elemento di tupla dedotti<br /><br />`false` - Indica la preferenza per i nomi di elemento di tupla espliciti |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2017 versione 15.6 |

Esempi di codice:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **ID regola** | IDE0037 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per i nomi di membro di tipo anonimo dedotti<br /><br />`false` - Indica la preferenza per i nomi di membro di tipo anonimo espliciti |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2017 versione 15.6 |

Esempi di codice:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_style\_prefer\_auto\_properties

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_auto_properties |
| **ID regola** | IDE0032 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per le proprietà automatiche rispetto alle proprietà con campi sottostanti privati<br /><br />`false` - Indica la preferenza per le proprietà con campi sottostanti privati rispetto alle proprietà automatiche |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |

Esempi di codice:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID regola** | IDE0041 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per l'uso di un controllo Null con criteri di ricerca anziché `object.ReferenceEquals`<br /><br />`false` - Indica la preferenza per `object.ReferenceEquals` anziché per un controllo Null con criteri di ricerca |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |

Esempi di codice:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_conditional_expression_over_assignment |
| **ID regola** | IDE0045 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per le assegnazioni con un'istruzione condizionale ternaria anziché un'istruzione if-else<br /><br />`false` - Indica la preferenza per le assegnazioni con un'istruzione if-else anziché un'istruzione condizionale ternaria |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2017 versione 15.8 |

Esempi di codice:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_conditional_expression_over_return |
| **ID regola** | IDE0046 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza che le istruzioni return usino un'istruzione condizionale ternaria anziché un'istruzione if-else<br /><br />`false` - Indica la preferenza che le istruzioni return usino un'istruzione if-else anziché un'istruzione condizionale ternaria |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2017 versione 15.8 |

Esempi di codice:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_style\_prefer\_compound\_assignment

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_compound_assignment |
| **ID regola** | IDE0054 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per le espressioni di [assegnazione composta](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false` - Non indica la preferenza per le espressioni di assegnazione composta |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Preferenze di controllo dei valori Null

Le regole di stile in questa sezione riguardano le preferenze di controllo dei valori Null.

Queste regole possono essere visualizzate in un file *.editorconfig* come indicato di seguito:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Nome regola** | dotnet_style_coalesce_expression |
| **ID regola** | IDE0029 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `true` - Indica la preferenza per le espressioni di unione Null rispetto al controllo degli operatori ternari<br /><br />`false` - Indica la preferenza per il controllo degli operatori ternari rispetto alle espressioni di unione Null |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Nome regola** | dotnet_style_null_propagation |
| **ID regola** | IDE0031 |
| **Lingue applicabili** | C# 6.0+ e Visual Basic 14+ |
| **Valori** | `true` - Indica la preferenza per l'uso dell'operatore condizionale Null, laddove possibile<br /><br />`false` - Indica la preferenza per l'uso del controllo Null ternario, laddove possibile |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Nome regola** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **ID regola** | IDE0041 |
| **Lingue applicabili** | C# 6.0+ e Visual Basic 14+ |
| **Valori** | `true`- Prefer è un controllo null rispetto al metodo di uguaglianza dei riferimenti<br /><br />`false`- Preferisci il metodo di uguaglianza dei riferimenti rispetto al controllo null- Prefer reference equality method over is null check |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

## <a name="net-code-quality-settings"></a>Impostazioni di qualità del codice .NET

Le regole di qualità illustrate in questa sezione si applicano al codice C# e Visual Basic. Vengono usate per configurare gli analizzatori del codice integrati nell'IDE (Integrated Development Environment) di Visual Studio. Per informazioni sulla configurazione di analizzatori FxCop con un file EditorConfig, vedere [Configurare gli analizzatori FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Preferenze per i parametri](#parameter-preferences)
  - dotnet\_code\_quality\_unused\_parameters

### <a name="parameter-preferences"></a>Preferenze per i parametri

Le regole di qualità illustrate in questa sezione riguardano i parametri dei metodi.

Queste regole possono essere visualizzate in un file *.editorconfig* come indicato di seguito:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_code\_quality\_unused\_parameters

|||
|-|-|
| **Nome regola** | dotnet_code_quality_unused_parameters |
| **ID regola** | IDE0060 |
| **Lingue applicabili** | C# e Visual Basic |
| **Valori** | `all` - Contrassegna i metodi con qualsiasi accessibilità che contengono parametri non usati<br /><br />`non_public` - Contrassegna solo i metodi non pubblici che contengono parametri non usati |
| **Impostazione predefinita di Visual Studio** | `all:suggestion` |

Esempi di codice:

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>Impostazioni di stile del codice C#

Le regole di stile illustrate in questa sezione sono applicabili solo a C#.

- [Tipi impliciti ed espliciti](#implicit-and-explicit-types)
  - csharp\_style\_var\_for\_built\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - csharp\_style\_var_elsewhere
- [Membri con corpo di espressione](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - csharp\_style\_expression\_bodied_lambdas
  - csharp\_style\_expression\_bodied\_local_functions
- [Criteri](#pattern-matching)
  - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
  - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [Dichiarazioni di variabili inline](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [Preferenze a livello di espressione](#c-expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
- [Preferenze di controllo "Null"](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [Preferenze modificatore](#normalize-modifiers) \_-csharp modifier_order preferiti\_
- [Preferenze blocco codice](#code-block-preferences)
  - csharp\_prefer_braces
- [Preferenze per i valori non usati](#unused-value-preferences)
  - csharp\_style\_unused\_value\_expression\_statement_preference
  - csharp\_style\_unused\_value\_assignment_preference
- [Preferenze per indici e intervalli](#index-and-range-preferences)
  - csharp\_style\_prefer\_index_operator
  - csharp\_style\_prefer\_range_operator
- [Preferenze varie](#miscellaneous-preferences)
  - csharp\_style\_deconstructed\_variable_declaration
  - csharp\_style\_pattern\_local\_over\_anonymous_function
  - csharp\_using\_directive\_placement
  - csharp\_prefer\_static\_local_function
  - csharp\_prefer\_simple\_using_statement
  - csharp\_style\_prefer\_switch_expression

### <a name="implicit-and-explicit-types"></a>Tipi impliciti ed espliciti

Le regole di stile illustrate in questa sezione riguardano l'uso della parola chiave [var](/dotnet/csharp/language-reference/keywords/var) rispetto a un tipo esplicito in una dichiarazione di variabile. Questa regola può essere applicata separatamente ai tipi predefiniti, quando il tipo è apparente, e altrove.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_style\_var\_for\_built\_in_types

|||
|-|-|
| **Nome regola** | csharp_style_var_for_built_in_types |
| **ID regola** | IDE0007 e IDE0008 |
| **Lingue applicabili** | C#  |
| **Valori** | `true` - Indica la preferenza a usare `var` per dichiarare le variabili con tipi di sistema predefiniti, ad esempio `int`<br /><br />`false` - Indica la preferenza a usare un tipo esplicito anziché `var` per dichiarare le variabili con tipi di sistema predefiniti, ad esempio `int` |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Nome regola** | csharp_style_var_when_type_is_apparent |
| **ID regola** | IDE0007 e IDE0008 |
| **Lingue applicabili** | C#  |
| **Valori** | `true` - Indica la preferenza per `var` quando il tipo è già menzionato nel lato destro di un'espressione di dichiarazione<br /><br />`false` - Indica la preferenza a usare un tipo esplicito anziché `var` quando il tipo è già menzionato nel lato destro di un'espressione di dichiarazione |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_style\_var_elsewhere

|||
|-|-|
| **Nome regola** | csharp_style_var_elsewhere |
| **ID regola** | IDE0007 e IDE0008 |
| **Lingue applicabili** | C#  |
| **Valori** | `true` - Indica la preferenza per `var` rispetto a un tipo esplicito in tutti i casi, a meno che non venga sostituita da un'altra regola di stile del codice<br /><br />`false` - Indica la preferenza per un tipo esplicito rispetto a `var` in tutti i casi, a meno che non venga sostituito da un'altra regola di stile del codice |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Membri con corpo di espressione

Le regole di stile illustrate in questa sezione riguardano l'uso di [membri con corpo di espressione](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) quando la logica è costituita da una sola espressione. Questa regola può essere applicata a metodi, costruttori, operatori, proprietà, indicizzatori e funzioni di accesso.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_methods |
| **ID regola** | IDE0022 |
| **Lingue applicabili** | C# 6.0+  |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per i metodi<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per i metodi quando sono a riga singola<br /><br />`false` - Indica la preferenza per i corpi di blocco per i metodi |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_constructors |
| **ID regola** | IDE0021 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per i costruttori<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per i costruttori quando sono a riga singola<br /><br />`false` - Indica la preferenza per i corpi di blocco per i costruttori |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_operators |
| **ID regola** | IDE0023 e IDE0024 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per gli operatori<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per gli operatori quando sono a riga singola<br /><br />`false` - Indica la preferenza per i corpi di blocco per gli operatori |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_properties |
| **ID regola** | IDE0025 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per le proprietà<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per le proprietà quando sono a riga singola<br /><br />`false` - Indica la preferenza per i corpi di blocco per le proprietà |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_indexers |
| **ID regola** | IDE0026 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per gli indicizzatori<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per gli indicizzatori quando sono a riga singola<br /><br />`false` - Indica la preferenza per i corpi di blocco per gli indicizzatori |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_accessors |
| **ID regola** | IDE0027 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per le funzioni di accesso<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per le funzioni di accesso quando sono a riga singola<br /><br />`false` - Indica la preferenza per i corpi di blocco per le funzioni di accesso |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>csharp\_style\_expression\_bodied_lambdas

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_lambdas |
| **ID regola** | IDE0053 |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per le espressioni lambda<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per le espressioni lambda quando sono a riga singola<br /><br />`false` - Indica la preferenza dei corpi di blocco per le espressioni lambda |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>csharp\_style\_expression\_bodied\_local_functions

A partire dalla versione 7.0, C# supporta le [funzioni locali](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Le funzioni locali sono metodi privati di un tipo annidati in un altro membro.

|||
|-|-|
| **Nome regola** | csharp_style_expression_bodied_local_functions |
| **ID regola** | IDE0061 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza dei corpi di espressione per le funzioni locali<br /><br />`when_on_single_line` - Indica la preferenza dei corpi di espressione per le funzioni locali quando sono a riga singola<br /><br />`false` - Indica la preferenza dei corpi di blocco per le funzioni locali |
| **Impostazione predefinita di Visual Studio** | `false:silent` |

Esempi di codice:

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>Corrispondenza dei criteri

Le regole di stile illustrate in questa sezione riguardano l'uso dei [criteri di ricerca](/dotnet/csharp/pattern-matching) in C#.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|||
|-|-|
| **Nome regola** | csharp_style_pattern_matching_over_is_with_cast_check |
| **ID regola** | IDE0020 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza per i criteri di ricerca invece delle espressioni `is` con i cast di tipo<br /><br />`false` - Indica la preferenza per le espressioni `is` con i cast di tipo invece dei criteri di ricerca |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|||
|-|-|
| **Nome regola** | csharp_style_pattern_matching_over_as_with_null_check |
| **ID regola** | IDE0019 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza per i criteri di ricerca invece delle espressioni `as` con i controlli Null per determinare se un elemento è di un determinato tipo<br /><br />`false` - Indica la preferenza per le espressioni `as` con i controlli Null invece dei criteri di ricerca per determinare se un elemento è di un determinato tipo |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Dichiarazioni di variabili inline

Questa regola di stile riguarda la possibilità o meno di dichiarare le variabili `out` inline. A partire da C# 7 è possibile [dichiarare una variabile out nell'elenco di argomenti di una chiamata al metodo](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument) anziché in una dichiarazione di variabile separata.

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Nome regola** | csharp_style_inlined_variable_declaration |
| **ID regola** | IDE0018 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza a dichiarare le variabili `out` inline nell'elenco di argomenti di una chiamata al metodo, laddove possibile<br /><br />`false` - Indica la preferenza a dichiarare le variabili `out` prima della chiamata al metodo |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>Preferenze a livello di espressione C#

Le regole di stile illustrate in questa sezione riguardano le preferenze a livello di espressione.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_prefer\_simple\_default_expression

Questa regola di stile riguarda l'utilizzo del [ `default` valore letterale per](/dotnet/csharp/language-reference/operators/default#default-literal) le espressioni di valore predefinito quando il compilatore può dedurre il tipo dell'espressione.

|||
|-|-|
| **Nome regola** | csharp_prefer_simple_default_expression |
| **ID regola** | IDE0034 |
| **Lingue applicabili** | C# 7.1+  |
| **Valori** | `true` - Indica la preferenza per `default` rispetto a `default(T)`<br /><br />`false` - Indica la preferenza per `default(T)` rispetto a `default` |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>Preferenze di controllo dei valori Null C#

Queste regole di stile riguardano la sintassi relativa al controllo `null`, incluso l'uso delle espressioni `throw` o delle istruzioni `throw`, nonché la possibilità di eseguire un controllo Null o usare l'operatore di unione condizionale (`?.`) quando viene chiamata un'[espressione lambda](/dotnet/csharp/lambda-expressions).

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Nome regola** | csharp_style_throw_expression |
| **ID regola** | IDE0016 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza per l'uso di espressioni `throw` anziché di istruzioni `throw`<br /><br />`false` - Indica la preferenza per l'uso di istruzioni `throw` anziché di espressioni `throw` |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Nome regola** | csharp_style_conditional_delegate_call |
| **ID regola** | IDE0041 |
| **Lingue applicabili** | C# 6.0+  |
| **Valori** | `true` - Indica la preferenza a usare l'operatore di unione condizionale (`?.`) quando si chiama un'espressione lambda, anziché eseguire un controllo Null<br /><br />`false` - Indica la preferenza a eseguire un controllo Null prima di chiamare un'espressione lambda, anziché usare l'operatore di unione condizionale (`?.`) |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Preferenze per i blocchi di codice

Questa regola di stile riguarda l'uso delle parentesi graffe `{ }` per racchiudere i blocchi di codice.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_prefer\_braces

|||
|-|-|
| **Nome regola** | csharp_prefer_braces |
| **ID regola** | IDE0011 |
| **Lingue applicabili** | C# |
| **Valori** | `true` - Indica la preferenza a usare le parentesi graffe anche per una riga di codice<br /><br />`false` - Indica la preferenza a non usare le parentesi graffe se consentito<br /><br />`when_multiline`- Preferisci le parentesi graffe su più righe |
| **Impostazione predefinita di Visual Studio** | `true:silent` |

Esempi di codice:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Preferenze per i valori non usati

Queste regole di stile riguardano le espressioni non usate e le assegnazioni di valori.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|||
|-|-|
| **Nome regola** | csharp_style_unused_value_expression_statement_preference |
| **ID regola** | IDE0058 |
| **Lingue applicabili** | C# |
| **Valori** | `discard_variable` - Indica la preferenza ad assegnare un'espressione non usata a una variabile [discard](/dotnet/csharp/discards) <br /><br />`unused_local_variable` - Indica la preferenza ad assegnare un'espressione non usata a una variabile locale |
| **Impostazione predefinita di Visual Studio** | `discard_variable:silent` |

Esempi di codice:

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|||
|-|-|
| **Nome regola** | csharp_style_unused_value_assignment_preference |
| **ID regola** | IDE0059 |
| **Lingue applicabili** | C# |
| **Valori** | `discard_variable` - Indica la preferenza a usare una variabile [discard](/dotnet/csharp/discards) quando si assegna un valore non usato<br /><br />`unused_local_variable` - Indica la preferenza a usare una variabile locale quando si assegna un valore non usato |
| **Impostazione predefinita di Visual Studio** | `discard_variable:suggestion` |

Esempi di codice:

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>Preferenze per indici e intervalli

Queste regole di stile riguardano l'uso degli operatori di indice e intervallo disponibili in C# 8.0 e versioni successive.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_style\_prefer\_index_operator

|||
|-|-|
| **Nome regola** | csharp_style_prefer_index_operator |
| **ID regola** | IDE0056 |
| **Lingue applicabili** | C# 8.0+ |
| **Valori** | `true` - Indica la preferenza a usare l'operatore `^` quando si calcola un indice dalla fine di una raccolta<br /><br />`false` - Non indica la preferenza a usare l'operatore `^` quando si calcola un indice dalla fine di una raccolta |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_style\_prefer\_range_operator

|||
|-|-|
| **Nome regola** | csharp_style_prefer_range_operator |
| **ID regola** | IDE0057 |
| **Lingue applicabili** | C# 8.0+ |
| **Valori** | `true` - Indica la preferenza a usare l'operatore di intervallo `..` quando si estrae una "sezione" di una raccolta<br /><br />`false` - Non indica la preferenza a usare l'operatore di intervallo `..` quando si estrae una "sezione" di una raccolta |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>Preferenze varie

Questa sezione contiene varie regole di stile.

Esempio di file *.editorconfig:*

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_style\_deconstructed\_variable_declaration

|||
|-|-|
| **Nome regola** | csharp_style_deconstructed_variable_declaration |
| **ID regola** | IDE0042 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza per la dichiarazione di variabili decostruite<br /><br />`false` - Non indica la preferenza per la decostruzione nelle dichiarazioni di variabili |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

A partire dalla versione 7.0, C# supporta le [funzioni locali](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Le funzioni locali sono metodi privati di un tipo annidati in un altro membro.

|||
|-|-|
| **Nome regola** | csharp_style_pattern_local_over_anonymous_function |
| **ID regola** | IDE0039 |
| **Lingue applicabili** | C# 7.0+ |
| **Valori** | `true` - Indica la preferenza per le funzioni locali rispetto alle funzioni anonime<br /><br />`false` - Indica la preferenza per le funzioni anonime rispetto alle funzioni locali |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

#### <a name="csharp_using_directive_placement"></a>csharp\_using\_directive_placement

|||
|-|-|
| **Nome regola** | csharp_using_directive_placement |
| **ID regola** | IDE0065 |
| **Lingue applicabili** | C# |
| **Valori** | `outside_namespace` - Indica la preferenza a posizionare le direttive `using` all'esterno dello spazio dei nomi<br /><br />`inside_namespace` - Indica la preferenza a posizionare le direttive `using` all'interno dello spazio dei nomi |
| **Impostazione predefinita di Visual Studio** | `outside_namespace:silent` |

Esempi di codice:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_prefer\_static\_local_function

|||
|-|-|
| **Nome regola** | csharp_prefer_static_local_function |
| **ID regola** | IDE0062 |
| **Lingue applicabili** | C# 8.0+ |
| **Valori** | `true` - Indica la preferenza a contrassegnare le funzioni locali come `static`<br /><br />`false` - Non indica la preferenza a contrassegnare le funzioni locali come `static` |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_prefer\_simple\_using_statement

|||
|-|-|
| **Nome regola** | csharp_prefer_simple_using_statement |
| **ID regola** | IDE0063 |
| **Lingue applicabili** | C# 8.0+ |
| **Valori** | `true`- Preferire usare una *semplice* `using` affermazione<br /><br />`false`- Non preferire usare una *semplice* `using` affermazione |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |

Esempi di codice:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_style\_prefer\_switch_expression

|||
|-|-|
| **Nome regola** | csharp_style_prefer_switch_expression |
| **ID regola** | IDE0066 |
| **Lingue applicabili** | C# 8.0+ |
| **Valori** | `true` - Indica la preferenza a usare un'espressione `switch` (introdotta con C# 8.0)<br /><br />`false` - Indica la preferenza a usare un'[istruzione switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Impostazione predefinita di Visual Studio** | `true:suggestion` |
| **Versione introdotta** | Visual Studio 2019 versione 16.2 |

Esempi di codice:

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>Vedere anche

- [Convenzioni di formattazione](editorconfig-formatting-conventions.md)
- [Convenzioni di denominazione](editorconfig-naming-conventions.md)
- [Impostazioni della convenzione di codifica .NET per EditorConfig](editorconfig-code-style-settings-reference.md)
