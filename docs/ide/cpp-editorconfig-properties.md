---
title: Convenzioni di formattazione C++ EditorConfig
titleSuffix: ''
description: Informazioni su come usare EditorConfig per formattare il codice C++ in Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jillfra
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 31a7db73a4487267c2a74fe628d28b577d339aba
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078841"
---
# <a name="c-editorconfig-formatting-conventions"></a>Convenzioni di formattazione C++ EditorConfig

Il formattatore di Visual Studio C++ dispone di un set completo di impostazioni configurabili che è possibile applicare a livello globale. Per impostare le impostazioni di formattazione C++ per un'area di lavoro specifica, usare [clangformat](https://clang.llvm.org/docs/ClangFormat.html) o [EditorConfig](https://editorconfig.org/). Visual Studio e Visual Studio Code includono il supporto EditorConfig incorporato per ognuna delle impostazioni di formattazione globali di Visual Studio C++, con le impostazioni EditorConfig che hanno la precedenza. Ciò significa che è possibile aggiungere i file EditorConfig all'area di lavoro per configurare la formattazione C++ a un livello più granulare e applicare uno stile di codice coerente per tutti gli utenti che contribuiscono al progetto.

## <a name="c-formatting-conventions"></a>Convenzioni di formattazione C++

Le impostazioni di EditorConfig per la formattazione C++ sono precedute dal prefisso `_cpp__` . Di seguito è riportato un esempio di come potrebbe essere il file EditorConfig:

```ini
[\*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Nella parte restante di questo documento sono elencate tutte le impostazioni di formattazione C++ di EditorConfig supportate da Visual Studio e VS Code.

### <a name="indentation-settings"></a>Impostazioni rientro

**Rientro parentesi graffe**

- Nome: `cpp_indent_braces`
- Valori: `true` , `false`

**Rientro di ogni riga relativamente a**

- Nome: `cpp_indent_multi_line_relative_to`
- Valori:
  - `outermost_parenthesis` -Quando viene digitata una nuova riga, viene rientrata relativamente alla parentesi di apertura più esterna.
  - `innermost_parenthesis` -Quando viene digitata una nuova riga, viene rientrata relativamente alla parentesi di apertura più interna.
  - `statement_begin` -Quando viene digitata una nuova riga, viene rientrata relativamente all'inizio dell'istruzione corrente.

**Allinea tra parentesi le nuove righe quando digitate**

- Nome: `cpp_indent_within_parentheses`
- Valori:
  - `align_to_parenthesis` -Allinea il contenuto alla parentesi di apertura.
  - `indent` -Rientra le nuove righe.

**Nel codice esistente, non usare l'impostazione per l'allineamento delle nuove righe tra parentesi**

- Nome: `cpp_indent_preserve_within_parentheses`
- Valori: `true` , `false`

**Rientra contenuto case**

- Nome: `cpp_indent_case_contents`
- Valori: `true` , `false`

**Rientro etichette case**

- Nome: `cpp_indent_case_labels`
- Valori: `true` , `false`

**Rientra le parentesi graffe dopo un'istruzione case**

- Nome: `cpp_indent_case_contents_when_block`
- Valori: `true` , `false`

**Rientro parentesi graffe di espressioni lambda usate come parametri**

- Nome: `cpp_indent_lambda_braces_when_parameter`
- Valori: `true` , `false`

**Posizione delle etichette GOTO**

- Nome: `cpp_indent_goto_labels`
- Valori:
  - `one_left` -Un rientro a sinistra
  - `leftmost_column` -Passa alla colonna più a sinistra
  - `none` -Lascia rientri

**Posizione delle direttive per il preprocessore**

- Nome: `cpp_indent_preprocessor`
- Valori:
  - `one_left` -Un rientro a sinistra
  - `leftmost_column` -Passa alla colonna più a sinistra
  - `none` -Lascia rientri

**Rientro identificatori di accesso**

- Nome: `cpp_indent_access_specifiers`
- Valori: `true` , `false`

**Rientro contenuto spazio dei nomi**

- Nome: `cpp_indent_namespace_contents`
- Valori: `true` , `false`

**Mantieni rientro dei commenti**

- Nome: `cpp_indent_preserve_comments`
- Valori: `true` , `false`

### <a name="newline-settings"></a>Impostazioni di nuova riga

**Posizione parentesi graffe di apertura per gli spazi dei nomi**

- Nome: `cpp_new_line_before_open_brace_namespace`
- Valori:
  - `new_line` -Sposta in una nuova riga
  - `same_line` -Mantieni sulla stessa riga, ma Aggiungi uno spazio prima
  - `ignore` -Non riposizionare automaticamente

**Posizione parentesi graffe di apertura per i tipi**

- Nome: `cpp_new_line_before_open_brace_type`
- Valori:
  - `new_line` -Sposta in una nuova riga
  - `same_line` -Mantieni sulla stessa riga, ma Aggiungi uno spazio prima
  - `ignore` -Non riposizionare automaticamente

**Posizione parentesi graffe di apertura per le funzioni**

- Nome: `cpp_new_line_before_open_brace_function`
- Valori:
  - `new_line` -Sposta in una nuova riga
  - `same_line` -Mantieni sulla stessa riga, ma Aggiungi uno spazio prima
  - `ignore` -Non riposizionare automaticamente

**Posizione parentesi graffe di apertura per i blocchi di controllo**

- Nome: `cpp_new_line_before_open_brace_block`
- Valori:
  - `new_line` -Sposta in una nuova riga
  - `same_line` -Mantieni sulla stessa riga, ma Aggiungi uno spazio prima
  - `ignore` -Non riposizionare automaticamente

**Posizione parentesi graffe di apertura per le espressioni lambda**

- Nome: `cpp_new_line_before_open_brace_lambda`
- Valori:
  - `new_line` -Sposta in una nuova riga
  - `same_line` -Mantieni sulla stessa riga, ma Aggiungi uno spazio prima
  - `ignore` -Non riposizionare automaticamente
 
**Inserisci parentesi graffe di ambito su righe separate**

- Nome: `cpp_new_line_scope_braces_on_separate_lines`
- Valori: `true` , `false`

**Per i tipi vuoti, spostare le parentesi graffe di chiusura nella stessa riga delle parentesi graffe di apertura**

- Nome: `cpp_new_line_close_brace_same_line_empty_type`
- Valori: `true` , `false`

**Per corpi di funzioni vuoti, spostare le parentesi graffe di chiusura nella stessa riga delle parentesi graffe di apertura**

- Nome: `cpp_new_line_close_brace_same_line_empty_function`
- Valori: `true` , `false`

**Inserisci ' Catch ' e parole chiave simili in una nuova riga**

- Nome: `cpp_new_line_before_catch`
- Valori: `true` , `false`

**Inserisci ' else ' in una nuova riga**

- Nome: `cpp_new_line_before_else`
- Valori: `true` , `false`

**Inserisci ' while ' in un ciclo do-while in una nuova riga**

- Nome: `cpp_new_line_before_while_in_do_while`
- Valori: `true` , `false`

### <a name="spacing-settings"></a>Impostazioni spaziatura

**Spaziatura tra i nomi di funzione e le parentesi di apertura degli elenchi di argomenti**

- Nome: `cpp_space_before_function_open_parenthesis`
- Valori:
  - `insert` -Inserisci uno spazio
  - `remove` -Rimuovi spazi
  - `ignore` -Non modificare gli spazi

**Inserisci uno spazio tra le parentesi di un elenco di argomenti**

- `cpp_space_within_parameter_list_parentheses`Valori nome: `true` ,`false`

**Inserisci uno spazio tra le parentesi quando l'elenco di argomenti è vuoto**

- Nome: `cpp_space_between_empty_parameter_list_parentheses`
- Valori: `true` , `false`

**Inserisci spazio tra la parola chiave e le parentesi di apertura nelle istruzioni del flusso di controllo**

- Nome: `cpp_space_after_keywords_in_control_flow_statements`
- Valori: `true` , `false`

**Inserisci uno spazio tra le parentesi di un'istruzione di controllo**

- Nome: `cpp_space_within_control_flow_statement_parentheses`
- Valori: `true` , `false`

**Inserisci spazio prima delle parentesi di apertura degli elenchi di argomenti lambda**

- Nome: `cpp_space_before_lambda_open_parenthesis`
- Valori: `true` , `false`

**Inserisci uno spazio tra le parentesi di un cast di tipo C**

- Nome: `cpp_space_within_cast_parentheses`
- Valori: `true` , `false`

**Inserisci spazio dopo le parentesi di chiusura del cast di tipo C**

- Nome: `cpp_space_after_cast_close_parenthesis`
- Valori: `true` , `false`

**Inserisci uno spazio tra le parentesi di un'espressione tra parentesi**

- Nome: `cpp_space_within_expression_parentheses`
- Valori: `true` , `false`

**Inserisci spazio prima della parentesi graffa di apertura dei blocchi**

- Nome: `cpp_space_before_block_open_brace`
- Valori: `true` , `false`

**Inserisci spazio tra parentesi graffe vuote**

- Nome: `cpp_space_between_empty_braces`
- Valori: `true` , `false`

**Inserisci spazio prima della parentesi graffa di apertura dell'inizializzazione uniforme e degli elenchi di inizializzatori**

- Nome: `cpp_space_before_initializer_list_open_brace`
- Valori: `true` , `false`

**Inserisci uno spazio tra parentesi graffe di inizializzazione e elenchi di inizializzatori uniformi**

- Nome: `cpp_space_within_initializer_list_braces`
- Valori: `true` , `false`

**Mantieni gli spazi all'interno degli elenchi di inizializzazione e inizializzazione uniforme**

- Nome: `cpp_space_preserve_in_initializer_list`
- Valori: `true` , `false`

**Inserisci spazio prima delle parentesi quadre di apertura**

- Nome: `cpp_space_before_open_square_bracket`
- Valori: `true` , `false`

**Inserisci spazio tra parentesi quadre**

- Nome: `cpp_space_within_square_brackets`
- Valori: `true` , `false`

**Inserisci spazio prima delle parentesi quadre vuote**

- Nome: `cpp_space_before_empty_square_brackets`
- Valori: `true` , `false`

**Inserisci spazio tra parentesi quadre vuote**

- Nome: `cpp_space_between_empty_square_brackets`
- Valori: `true` , `false`

**Raggruppa le parentesi quadre per le matrici multidimensionali**

- Nome: `cpp_space_group_square_brackets`
- Valori: `true` , `false`

**Inserisci uno spazio tra parentesi quadre per le espressioni lambda**

- Nome: `cpp_space_within_lambda_brackets`
- Valori: `true` , `false`

**SpaceBetweenEmptyLambdaBrackets**

- Nome: `cpp_space_between_empty_lambda_brackets`
- Valori: `true` , `false`

**Inserisci spazio prima delle virgole**

- Nome: `cpp_space_before_comma`
- Valori: `true` , `false`

**Inserisci spazio dopo le virgole**

- Nome: `cpp_space_after_comma`
- Valori: `true` , `false`

**Rimuovere gli spazi prima e dopo gli operatori membro**

- Nome: `cpp_space_remove_around_member_operators`
- Valori: `true` , `false`

**Inserisci spazio prima dei due punti per base nelle dichiarazioni di tipo**

- Nome: `cpp_space_before_inheritance_colon`
- Valori: `true` , `false`

**Inserisci spazio prima dei due punti per i costruttori**

- Nome: `cpp_space_before_constructor_colon`
- Valori: `true` , `false`

**Rimuovi spazio prima del punto e virgola**

- Nome: `cpp_space_remove_before_semicolon`
- Valori: `true` , `false`

**Inserisci spazio dopo il punto e virgola**

- Nome: `cpp_space_after_semicolon`
- Valori: `true` , `false`

**Rimuovere gli spazi tra gli operatori unari e i relativi operandi**

- Nome: `cpp_space_remove_around_unary_operator`
- Valori: `true` , `false`

**Spaziatura per operatori binari**

- Nome: `cpp_space_around_binary_operator`
- Valori:
  - `insert` -Inserisce gli spazi prima e dopo gli operatori binari.
  - `remove` -Rimuovere gli spazi intorno agli operatori binari.
  - `ignore` -Non modificare gli spazi intorno agli operatori binari.

**Spaziatura per gli operatori di assegnazione**

- Nome: `cpp_space_around_assignment_operator`
- Valori:
  - `insert` -Inserire gli spazi intorno agli operatori di assegnazione.
  - `remove` -Rimuovere gli spazi intorno agli operatori di assegnazione.
  - `ignore` -Non modificare gli spazi intorno agli operatori di assegnazione.

**Allineamento puntatore/riferimento**

- Nome: `cpp_space_pointer_reference_alignment`
- Valori:
  - `left` -Allinea a sinistra.
  - `center` -Allinea al centro.
  - `right` -Allinea a destra.
  - `ignore` -Lasciare invariato.

**Spaziatura per operatori condizionali**

- Nome: `cpp_space_around_ternary_operator`
- Valori:
  - `insert` -Inserire gli spazi intorno agli operatori condizionali.
  - `remove` -Rimuovere gli spazi intorno agli operatori condizionali.
  - `ignore` -Non modificare gli spazi intorno agli operatori condizionali.

### <a name="wrapping-options"></a>Opzioni di ritorno a capo

**Opzioni di wrapping per i blocchi**

- Nome: `cpp_wrap_preserve_blocks`
- Valori:
  - `one_liners` -Non eseguire il wrapping di blocchi di codice a una riga.
  - `all_one_line_scopes` -Non eseguire il wrapping dei blocchi di codice in cui le parentesi graffe di apertura e chiusura sono nella riga successiva.
  - `never` -Applica sempre le impostazioni delle nuove righe per i blocchi.

## <a name="see-also"></a>Vedere anche

- [EditorConfig.org](https://editorconfig.org/)
- [Supporting EditorConfig for a language service](../extensibility/supporting-editorconfig.md) (Supporto di EditorConfig per un servizio di linguaggio)
- [Funzionalità dell'editor del codice](writing-code-in-the-code-and-text-editor.md)
