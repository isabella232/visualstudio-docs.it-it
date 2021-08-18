---
title: Convenzioni di formattazione EditorConfig in C++
titleSuffix: ''
description: Informazioni su come usare EditorConfig per formattare il codice C++ in Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: b7554e2038f0be8d72b96e8b53280faca498e772
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124074"
---
# <a name="c-editorconfig-formatting-conventions"></a>Convenzioni di formattazione EditorConfig in C++

Il Visual Studio formattatore C++ include un set di impostazioni configurabili che possono essere applicate a livello globale. Per impostare le impostazioni di formattazione C++ per un'area di lavoro specifica, usare [clangformat](https://clang.llvm.org/docs/ClangFormat.html) o [EditorConfig.](https://editorconfig.org/) Sia Visual Studio che Visual Studio Code hanno il supporto predefinito di EditorConfig per ognuna delle impostazioni di formattazione C++ globali di Visual Studio, con le impostazioni di EditorConfig che hanno la precedenza. Ciò significa che è possibile aggiungere file EditorConfig all'area di lavoro per configurare la formattazione C++ a un livello più granulare e applicare uno stile di codice coerente per tutti gli utenti che contribuiscono al progetto.

## <a name="c-formatting-conventions"></a>Convenzioni di formattazione C++

Le impostazioni editorConfig per la formattazione di C++ sono precedute dal prefisso `cpp_` . Di seguito è riportato un esempio dell'aspetto del file EditorConfig:

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Nella parte restante di questo documento sono elencate tutte le impostazioni di formattazione C++ di EditorConfig supportate Visual Studio e VS Code.

### <a name="indentation-settings"></a>Impostazioni di rientro

**Rientro parentesi graffe**

- Nome: `cpp_indent_braces`
- Valori: `true` , `false`

**Impostare un rientro relativamente per ogni riga**

- Nome: `cpp_indent_multi_line_relative_to`
- Valori:
  - `outermost_parenthesis` - Quando viene digitata una nuova riga, viene impostata un rientro relativamente alla parentesi aperta più esterna.
  - `innermost_parenthesis` - Quando viene digitata una nuova riga, viene impostata un rientro relativamente alla parentesi aperta più interna.
  - `statement_begin` - Quando viene digitata una nuova riga, viene impostata un rientro relativamente all'inizio dell'istruzione corrente.

**All'interno delle parentesi allineare le nuove righe quando le si digita**

- Nome: `cpp_indent_within_parentheses`
- Valori:
  - `align_to_parenthesis` - Allinea il contenuto alla parentesi aperta.
  - `indent` - Rientro delle nuove righe.

**Nel codice esistente non usare l'impostazione per l'allineamento delle nuove righe tra parentesi**

- Nome: `cpp_indent_preserve_within_parentheses`
- Valori: `true` , `false`

**Rientro del contenuto delle maiuscole/minuscole**

- Nome: `cpp_indent_case_contents`
- Valori: `true` , `false`

**Rientro etichette maiuscole/minuscole**

- Nome: `cpp_indent_case_labels`
- Valori: `true` , `false`

**Rientro delle parentesi graffe dopo un'istruzione case**

- Nome: `cpp_indent_case_contents_when_block`
- Valori: `true` , `false`

**Rientrare le parentesi graffe delle espressioni lambda usate come parametri**

- Nome: `cpp_indent_lambda_braces_when_parameter`
- Valori: `true` , `false`

**Posizione delle etichette goto**

- Nome: `cpp_indent_goto_labels`
- Valori:
  - `one_left` - Un rientro a sinistra
  - `leftmost_column` - Sposta nella colonna più a sinistra
  - `none` - Lasciare rientro

**Posizione delle direttive del preprocessore**

- Nome: `cpp_indent_preprocessor`
- Valori:
  - `one_left` - Un rientro a sinistra
  - `leftmost_column` - Sposta nella colonna più a sinistra
  - `none` - Lasciare rientro

**Imposta un rientro per gli identificatori di accesso**

- Nome: `cpp_indent_access_specifiers`
- Valori: `true` , `false`

**Rientro del contenuto dello spazio dei nomi**

- Nome: `cpp_indent_namespace_contents`
- Valori: `true` , `false`

**Mantenere il rientro dei commenti**

- Nome: `cpp_indent_preserve_comments`
- Valori: `true` , `false`

### <a name="newline-settings"></a>Impostazioni di nuova riga

**Posizione delle parentesi graffe aperte per gli spazi dei nomi**

- Nome: `cpp_new_line_before_open_brace_namespace`
- Valori:
  - `new_line` - Passare a una nuova riga
  - `same_line` - Mantenere la stessa riga, ma aggiungere uno spazio prima
  - `ignore` - Non riposizionare automaticamente

**Posizione delle parentesi graffe aperte per i tipi**

- Nome: `cpp_new_line_before_open_brace_type`
- Valori:
  - `new_line` - Passare a una nuova riga
  - `same_line` - Mantenere la stessa riga, ma aggiungere uno spazio prima
  - `ignore` - Non riposizionare automaticamente

**Posizione delle parentesi graffe aperte per le funzioni**

- Nome: `cpp_new_line_before_open_brace_function`
- Valori:
  - `new_line` - Passare a una nuova riga
  - `same_line` - Mantenere la stessa riga, ma aggiungere uno spazio prima
  - `ignore` - Non riposizionare automaticamente

**Posizione delle parentesi graffe aperte per i blocchi di controllo**

- Nome: `cpp_new_line_before_open_brace_block`
- Valori:
  - `new_line` - Passare a una nuova riga
  - `same_line` - Mantenere la stessa riga, ma aggiungere uno spazio prima
  - `ignore` - Non riposizionare automaticamente

**Posizione delle parentesi graffe aperte per le espressioni lambda**

- Nome: `cpp_new_line_before_open_brace_lambda`
- Valori:
  - `new_line` - Passare a una nuova riga
  - `same_line` - Mantenere la stessa riga, ma aggiungere uno spazio prima
  - `ignore` - Non riposizionare automaticamente
 
**Inserire le parentesi graffe dell'ambito in righe separate**

- Nome: `cpp_new_line_scope_braces_on_separate_lines`
- Valori: `true` , `false`

**Per i tipi vuoti, spostare le parentesi graffe di chiusura nella stessa riga delle parentesi graffe di apertura**

- Nome: `cpp_new_line_close_brace_same_line_empty_type`
- Valori: `true` , `false`

**Per i corpi di funzione vuoti, spostare le parentesi graffe di chiusura nella stessa riga delle parentesi graffe di apertura**

- Nome: `cpp_new_line_close_brace_same_line_empty_function`
- Valori: `true` , `false`

**Inserire "catch" e parole chiave simili in una nuova riga**

- Nome: `cpp_new_line_before_catch`
- Valori: `true` , `false`

**Inserire 'else' in una nuova riga**

- Nome: `cpp_new_line_before_else`
- Valori: `true` , `false`

**Inserire 'while' in un ciclo do-while in una nuova riga**

- Nome: `cpp_new_line_before_while_in_do_while`
- Valori: `true` , `false`

### <a name="spacing-settings"></a>Impostazioni di spaziatura

**Spaziatura tra i nomi delle funzioni e le parentesi di apertura degli elenchi di argomenti**

- Nome: `cpp_space_before_function_open_parenthesis`
- Valori:
  - `insert` - Inserire uno spazio
  - `remove` - Rimuovere gli spazi
  - `ignore` - Non modificare gli spazi

**Inserire spazio tra parentesi di un elenco di argomenti**

- Valori `cpp_space_within_parameter_list_parentheses` dei nomi: `true` , `false`

**Inserire spazio tra parentesi quando l'elenco di argomenti è vuoto**

- Nome: `cpp_space_between_empty_parameter_list_parentheses`
- Valori: `true` , `false`

**Inserire spazio tra la parola chiave e le parentesi di apertura nelle istruzioni del flusso di controllo**

- Nome: `cpp_space_after_keywords_in_control_flow_statements`
- Valori: `true` , `false`

**Inserire spazio tra parentesi di un'istruzione di controllo**

- Nome: `cpp_space_within_control_flow_statement_parentheses`
- Valori: `true` , `false`

**Inserire spazio prima di aprire parentesi di elenchi di argomenti lambda**

- Nome: `cpp_space_before_lambda_open_parenthesis`
- Valori: `true` , `false`

**Inserire spazio tra parentesi di un cast di tipo C**

- Nome: `cpp_space_within_cast_parentheses`
- Valori: `true` , `false`

**Inserire spazio dopo la parentesi di chiusura del cast di tipo C**

- Nome: `cpp_space_after_cast_close_parenthesis`
- Valori: `true` , `false`

**Inserire spazio tra parentesi di un'espressione tra parentesi**

- Nome: `cpp_space_within_expression_parentheses`
- Valori: `true` , `false`

**Inserire spazio prima di aprire una parentesi graffa di blocchi**

- Nome: `cpp_space_before_block_open_brace`
- Valori: `true` , `false`

**Inserire spazio tra parentesi graffe vuote**

- Nome: `cpp_space_between_empty_braces`
- Valori: `true` , `false`

**Inserire spazio prima di aprire la parentesi graffa di elenchi di inizializzazione e inizializzatori uniformi**

- Nome: `cpp_space_before_initializer_list_open_brace`
- Valori: `true` , `false`

**Inserire spazio tra parentesi graffe di elenchi di inizializzazione e inizializzatori uniformi**

- Nome: `cpp_space_within_initializer_list_braces`
- Valori: `true` , `false`

**Mantenere gli spazi all'interno di elenchi uniformi di inizializzazione e inizializzatore**

- Nome: `cpp_space_preserve_in_initializer_list`
- Valori: `true` , `false`

**Inserire spazio prima di aprire le parentesi quadre**

- Nome: `cpp_space_before_open_square_bracket`
- Valori: `true` , `false`

**Inserire spazio tra parentesi quadre**

- Nome: `cpp_space_within_square_brackets`
- Valori: `true` , `false`

**Inserire spazio prima delle parentesi quadre vuote**

- Nome: `cpp_space_before_empty_square_brackets`
- Valori: `true` , `false`

**Inserire spazio tra parentesi quadre vuote**

- Nome: `cpp_space_between_empty_square_brackets`
- Valori: `true` , `false`

**Raggruppare le parentesi quadre per le matrici multidimensionali**

- Nome: `cpp_space_group_square_brackets`
- Valori: `true` , `false`

**Inserire spazio tra parentesi quadre per le espressioni lambda**

- Nome: `cpp_space_within_lambda_brackets`
- Valori: `true` , `false`

**SpaceBetweenEmptyLambdaBrackets**

- Nome: `cpp_space_between_empty_lambda_brackets`
- Valori: `true` , `false`

**Inserire spazio prima delle virgole**

- Nome: `cpp_space_before_comma`
- Valori: `true` , `false`

**Inserire spazio dopo le virgole**

- Nome: `cpp_space_after_comma`
- Valori: `true` , `false`

**Rimuovere gli spazi prima e dopo gli operatori membro**

- Nome: `cpp_space_remove_around_member_operators`
- Valori: `true` , `false`

**Inserire spazio prima dei due punti per la base nelle dichiarazioni di tipo**

- Nome: `cpp_space_before_inheritance_colon`
- Valori: `true` , `false`

**Inserire spazio prima dei due punti per i costruttori**

- Nome: `cpp_space_before_constructor_colon`
- Valori: `true` , `false`

**Rimuovere lo spazio prima del punto e virgola**

- Nome: `cpp_space_remove_before_semicolon`
- Valori: `true` , `false`

**Inserire spazio dopo il punto e virgola**

- Nome: `cpp_space_after_semicolon`
- Valori: `true` , `false`

**Rimuovere gli spazi tra gli operatori unari e i relativi operandi**

- Nome: `cpp_space_remove_around_unary_operator`
- Valori: `true` , `false`

**Spaziatura per gli operatori binari**

- Nome: `cpp_space_around_binary_operator`
- Valori:
  - `insert` - Inserire spazi prima e dopo gli operatori binari.
  - `remove` - Rimuovere gli spazi intorno agli operatori binari.
  - `ignore` - Non modificare gli spazi intorno agli operatori binari.

**Spaziatura per gli operatori di assegnazione**

- Nome: `cpp_space_around_assignment_operator`
- Valori:
  - `insert` - Inserire spazi intorno agli operatori di assegnazione.
  - `remove` - Rimuovere gli spazi intorno agli operatori di assegnazione.
  - `ignore` - Non modificare gli spazi intorno agli operatori di assegnazione.

**Allineamento puntatore/riferimento**

- Nome: `cpp_space_pointer_reference_alignment`
- Valori:
  - `left` - Allinea a sinistra.
  - `center` - Allinea al centro.
  - `right` - Allinea a destra.
  - `ignore` - Lasciare invariato.

**Spaziatura per gli operatori condizionali**

- Nome: `cpp_space_around_ternary_operator`
- Valori:
  - `insert` - Inserire spazi intorno agli operatori condizionali.
  - `remove` - Rimuovere gli spazi intorno agli operatori condizionali.
  - `ignore` - Non modificare gli spazi intorno agli operatori condizionali.

### <a name="wrapping-options"></a>Opzioni di ritorno a capo

**Opzioni di ritorno a capo per i blocchi**

- Nome: `cpp_wrap_preserve_blocks`
- Valori:
  - `one_liners` - Non eseguire il wrapping di blocchi di codice su una riga.
  - `all_one_line_scopes` - Non eseguire il wrapping dei blocchi di codice in cui le parentesi graffe di apertura e chiusura si trovano nella riga successiva.
  - `never` - Applicare sempre le impostazioni Nuove righe per i blocchi.

## <a name="see-also"></a>Vedi anche

- [EditorConfig.org](https://editorconfig.org/)
- [Supporting EditorConfig for a language service](../extensibility/supporting-editorconfig.md) (Supporto di EditorConfig per un servizio di linguaggio)
- [Funzionalità dell'editor del codice](writing-code-in-the-code-and-text-editor.md)
