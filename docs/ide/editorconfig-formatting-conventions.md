---
title: Convenzioni di formattazione .NET per EditorConfig
ms.date: 06/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 340d8ca7f7b578ae952c0b5024cd6962f20a0dff
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67262794"
---
# <a name="formatting-conventions"></a>Convenzioni di formattazione

Le convenzioni di formattazione per EditorConfig per Visual Studio possono essere suddivise in due categorie:

- [Impostazioni di formattazione .NET](#net-formatting-settings)

- [Impostazioni di formattazione C#](#c-formatting-settings)

## <a name="rule-format"></a>Formato delle regole

Le regole per le convenzioni di formattazione hanno il formato seguente:

`rule_name = value`

Per molte regole, specificare `true` (preferire questo stile) o `false` (non preferire questo stile) per `value`. Per altre regole, specificare un valore come `flush_left` o `before_and_after` per descrivere quando e dove applicare la regola. Non specificare un livello di gravità.

## <a name="net-formatting-settings"></a>Impostazioni di formattazione .NET

Le regole di formattazione illustrate in questa sezione si applicano al codice C# e Visual Basic.

- [Organizzare direttive using](#organize-using-directives)
   - dotnet_sort_system_directives_first
   - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organizzare direttive using

Queste regole di formattazione riguardano l'ordinamento e la visualizzazione di direttive `using` e istruzioni `Imports`.

Esempio di file *.editorconfig*:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnetsortsystemdirectivesfirst"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Nome regola** | dotnet_sort_system_directives_first |
| **Linguaggi applicabili** | C# e Visual Basic |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Ordina le direttive `using` System.* in ordine alfabetico e le posiziona prima di altre direttive using.<br /><br />`false` - Non posiziona le direttive `using` System.* prima di altre direttive `using`. |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnetseparateimportdirectivegroups"></a>dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **Nome regola** | dotnet_separate_import_directive_groups |
| **Linguaggi applicabili** | C# e Visual Basic |
| **Versione introdotta** | Visual Studio 2017 versione 15.5 |
| **Valori** | `true` - Inserisce una riga vuota tra gruppi di direttive `using`.<br /><br />`false` - Non inserisce una riga vuota tra gruppi di direttive `using`. |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>Impostazioni di formattazione C#

Le regole di formattazione illustrate in questa sezione si applicano solo al codice C#.

- [Opzioni dei caratteri di nuova riga](#new-line-options)
   - csharp_new_line_before_open_brace
   - csharp_new_line_before_else
   - csharp_new_line_before_catch
   - csharp_new_line_before_finally
   - csharp_new_line_before_members_in_object_initializers
   - csharp_new_line_before_members_in_anonymous_types
   - csharp_new_line_between_query_expression_clauses
- [Opzioni di rientro](#indentation-options)
   - csharp_indent_case_contents
   - csharp_indent_switch_labels
   - csharp_indent_labels
- [Opzioni di spaziatura](#spacing-options)
   - csharp_space_after_cast
   - csharp_space_after_keywords_in_control_flow_statements
   - csharp_space_between_method_declaration_parameter_list_parentheses
   - csharp_space_between_method_call_parameter_list_parentheses
   - csharp_space_between_parentheses
   - csharp_space_before_colon_in_inheritance_clause
   - csharp_space_after_colon_in_inheritance_clause
   - csharp_space_around_binary_operators
   - csharp_space_between_method_declaration_empty_parameter_list_parentheses
   - csharp_space_between_method_call_name_and_opening_parenthesis
   - csharp_space_between_method_call_empty_parameter_list_parentheses
   - csharp_space_after_comma
   - csharp_space_after_dot
- [Opzioni di wrapping](#wrap-options)
   - csharp_preserve_single_line_statements
   - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Opzioni di nuova riga

Queste regole di formattazione riguardano l'uso di nuove righe per formattare il codice.

Esempio di file *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharpnewlinebeforeopenbrace"></a>csharp\_new\_line\_before\_open_brace

Questa regola riguarda il posizionamento di una parentesi graffa di apertura `{` nella stessa riga del codice precedente o in una nuova riga. Per questa regola, specificare **all**, **none** oppure uno o più elementi di codice, ad esempio **methods** o **properties**, per definire quando applicare questa regola. Per specificare più elementi di codice, separarli con una virgola (,).

|||
|-|-|
| **Nome regola** | csharp_new_line_before_open_brace |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `all` - Richiede che le parentesi graffe siano posizionate in una nuova riga per tutte le espressioni (stile "Allman").<br /><br />`none` - Richiede che le parentesi graffe siano posizionate nella stessa riga per tutte le espressioni ("K&R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Richiedono che le parentesi graffe siano posizionate in una nuova riga per l'elemento di codice specificato (stile "Allman"). |
| **Impostazione predefinita di Visual Studio** | `all` |

Esempi di codice:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharpnewlinebeforeelse"></a>csharp\_new\_line\_before_else

|||
|-|-|
| **Nome regola** | csharp_new_line_before_else |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Posiziona le istruzioni `else` in una nuova riga.<br /><br />`false` - Posiziona le istruzioni `else` nella stessa riga. |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharpnewlinebeforecatch"></a>csharp\_new\_line\_before_catch

|||
|-|-|
| **Nome regola** | csharp_new_line_before_catch |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Posiziona le istruzioni `catch` in una nuova riga.<br /><br />`false` - Posiziona le istruzioni `catch` nella stessa riga. |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharpnewlinebeforefinally"></a>csharp\_new\_line\_before_finally

|||
|-|-|
| **Nome regola** | csharp_new_line_before_finally |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Richiede che le istruzioni `finally` siano posizionate in una nuova riga dopo la parentesi graffa di chiusura.<br /><br />`false` - Richiede che le istruzioni `finally` siano posizionate nella stessa riga della parentesi graffa di chiusura. |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **Nome regola** | csharp_new_line_before_members_in_object_initializers |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Richiede che i membri degli inizializzatori di oggetto siano posizionati in righe separate<br /><br />`false` - Richiede che i membri degli inizializzatori di oggetto siano posizionati nella stessa riga |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **Nome regola** | csharp_new_line_before_members_in_anonymous_types |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Richiede che membri dei tipi anonimi siano posizionati in righe separate<br /><br />`false` - Richiede che i membri dei tipi anonimi siano posizionati nella stessa riga |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharpnewlinebetweenqueryexpressionclauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Nome regola** | csharp_new_line_between_query_expression_clauses |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Richiede che gli elementi delle clausole di espressione di query siano posizionati in righe separate<br /><br />`false` - Richiede che gli elementi delle clausole di espressione di query siano posizionati nella stessa riga |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>Opzioni di rientro

Queste regole di formattazione riguardano l'uso del rientro per formattare il codice.

Esempio di file *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="csharpindentcasecontents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **Nome regola** | csharp_indent_case_contents |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Imposta un rientro per il contenuto case `switch`<br /><br />`false` - Non imposta un rientro per il contenuto case `switch` |
| **Impostazione predefinita di Visual Studio** | `true` |

- Quando questa regola è impostata su **true**, i.
- Quando questa regola è impostata su **false**, d.

Esempi di codice:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharpindentswitchlabels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **Nome regola** | csharp_indent_switch_labels |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Imposta un rientro per le etichette `switch`<br /><br />`false` - Non imposta un rientro per le etichette `switch` |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharpindentlabels"></a>csharp\_indent_labels

|||
|-|-|
| **Nome regola** | csharp_indent_labels |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `flush_left` - Le etichette vengono posizionate nella colonna più a sinistra<br /><br />`one_less_than_current` - Le etichette vengono posizionate con un rientro minore rispetto al contesto corrente<br /><br />`no_change` - Le etichette vengono posizionate con lo stesso rientro del contesto corrente |
| **Impostazione predefinita di Visual Studio** | `no_change` |

Esempi di codice:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

### <a name="spacing-options"></a>Opzioni di spaziatura

Queste regole di formattazione riguardano l'uso degli spazi per formattare il codice.

Esempio di file *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_after_comma = true
csharp_space_after_dot = false
```

#### <a name="csharpspaceaftercast"></a>csharp\_space\_after_cast

|||
|-|-|
| **Nome regola** | csharp_space_after_cast |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Richiede uno spazio tra un cast e il valore<br /><br />`false` - _Non_ richiede spazi tra il cast e il valore |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharpspaceafterkeywordsincontrolflowstatements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Nome regola** | csharp_space_after_keywords_in_control_flow_statements |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Richiede uno spazio dopo una parola chiave in un'istruzione di un flusso di controllo, ad esempio un ciclo `for`<br /><br />`false` - _Non_ richiede spazi dopo una parola chiave in un'istruzione di un flusso di controllo, ad esempio un ciclo `for` |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Nome regola** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Inserisce uno spazio dopo la parentesi di apertura e prima della parentesi di chiusura dell'elenco di parametri di una dichiarazione di metodo<br /><br />`false` - Non inserisce spazi dopo la parentesi di apertura e prima della parentesi di chiusura dell'elenco di parametri di una dichiarazione di metodo |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Nome regola** | csharp_space_between_method_call_parameter_list_parentheses |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Inserisce uno spazio dopo la parentesi di apertura e prima della parentesi di chiusura della chiamata a un metodo<br /><br />`false` - Non inserisce spazi dopo la parentesi di apertura e prima della parentesi di chiusura della chiamata a un metodo |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Nome regola** | csharp_space_between_parentheses |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `control_flow_statements` - Inserisce uno spazio tra le parentesi delle istruzioni del flusso di controllo<br /><br />`expressions` - Inserisce uno spazio tra le parentesi delle espressioni<br /><br />`type_casts` - Inserisce uno spazio tra le parentesi dei cast di tipo |
| **Impostazione predefinita di Visual Studio** | `false` |

Se si omette questa regola o si usa un valore diverso da `control_flow_statements`, `expressions` o `type_casts`, l'impostazione non viene applicata.

Esempi di codice:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharpspacebeforecolonininheritanceclause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nome regola** | csharp_space_before_colon_in_inheritance_clause |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |
| **Valori** | `true` - Richiede uno spazio prima dei due punti per le basi o le interfacce in una dichiarazione del tipo<br /><br />`false` - _Non_ richiede spazi prima dei due punti per le basi o le interfacce in una dichiarazione del tipo |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharpspaceaftercolonininheritanceclause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nome regola** | csharp_space_after_colon_in_inheritance_clause |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |
| **Valori** | `true` - Richiede uno spazio dopo i due punti per le basi o le interfacce in una dichiarazione del tipo<br /><br />`false` - _Non_ richiede spazi dopo i due punti per le basi o le interfacce in una dichiarazione del tipo |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharpspacearoundbinaryoperators"></a>csharp\_space\_around\_binary_operators

|||
|-|-|
| **Nome regola** | csharp_space_around_binary_operators |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |
| **Valori** | `before_and_after` - Inserisce uno spazio prima e dopo l'operatore binario<br /><br />`none` - Rimuove gli spazi prima e dopo l'operatore binario<br /><br />`ignore` - Ignora gli spazi prima e dopo gli operatori binari |
| **Impostazione predefinita di Visual Studio** | `before_and_after` |

Se si omette questa regola, o si usa un valore diverso da `before_and_after`, `none` o `ignore`, l'impostazione non viene applicata.

Esempi di codice:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Nome regola** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |
| **Valori** | `true` - Inserisce uno spazio tra le parentesi dell'elenco parametri vuoto per una dichiarazione di metodo<br /><br />`false` - Rimuove uno spazio tra le parentesi dell'elenco parametri vuoto per una dichiarazione di metodo |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Nome regola** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |
| **Valori** | `true` - Inserisce uno spazio tra il nome della chiamata al metodo e la parentesi di apertura<br /><br />`false` - Rimuove uno spazio tra il nome della chiamata al metodo e la parentesi di apertura |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Nome regola** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.7 |
| **Valori** | `true` - Inserisce uno spazio tra le parentesi dell'elenco di argomenti vuoto<br /><br />`false` - Rimuove lo spazio tra le parentesi dell'elenco di argomenti vuoto |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **Nome regola** | csharp_space_after_comma |
| **Linguaggi applicabili** | C# |
| **Valori** | `true` - Inserisce uno spazio dopo una virgola<br /><br />`false` - Rimuove lo spazio dopo una virgola |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **Nome regola** | csharp_space_after_dot |
| **Linguaggi applicabili** | C# |
| **Valori** | `true` - Inserisce uno spazio dopo un punto<br /><br />`false` - Rimuove lo spazio dopo un punto |
| **Impostazione predefinita di Visual Studio** | `false` |

Esempi di codice:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

### <a name="wrap-options"></a>Opzioni di wrapping

Queste regole di formattazione riguardano l'uso di singole righe e righe separate per istruzioni e blocchi di codice.

Esempio di file *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharppreservesinglelinestatements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Nome regola** | csharp_preserve_single_line_statements |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Lascia le istruzioni e le dichiarazioni di membri nella stessa riga<br /><br />`false` - Lascia le istruzioni e le dichiarazioni di membri in righe diverse |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharppreservesinglelineblocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Nome regola** | csharp_preserve_single_line_blocks |
| **Linguaggi applicabili** | C# |
| **Versione introdotta** | Visual Studio 2017 versione 15.3 |
| **Valori** | `true` - Lascia il blocco di codice in una sola riga<br /><br />`false` - Lascia il blocco di codice in righe separate |
| **Impostazione predefinita di Visual Studio** | `true` |

Esempi di codice:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

## <a name="see-also"></a>Vedere anche

- [Convenzioni del linguaggio](editorconfig-language-conventions.md)
- [Convenzioni di denominazione](editorconfig-naming-conventions.md)
- [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](editorconfig-code-style-settings-reference.md)