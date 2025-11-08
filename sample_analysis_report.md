# Structured Design Analysis Report
**Project:** Unknown Project  
**Date:** 2025-11-08 18:48:53  
**Analysis Based On:** Constantine & Yourdon's "Structured Design" (1979)

---

## Executive Summary


- **Total Modules Analyzed:** 31
- **Average Cohesion Score:** 4.29/7
- **Modules with Coupling Issues:** 5

### Cohesion Distribution

- **Procedural**: 24 modules (77.4%)
- **Sequential**: 3 modules (9.7%)
- **Functional**: 2 modules (6.5%)
- **Logical**: 1 modules (3.2%)
- **Temporal**: 1 modules (3.2%)

---

## ✅ The Good: Exemplary Modules

*These modules demonstrate excellent Structured Design principles with high cohesion and low coupling.*


### `calculate_order_total`
- **File:** sample_ecommerce.py:53
- **Cohesion:** Sequential (Functional/Sequential)
- **Assessment:** High cohesion, low coupling - exemplifies Structured Design principles


### `validate_email_address`
- **File:** sample_ecommerce.py:101
- **Cohesion:** Functional (Functional/Sequential)
- **Assessment:** High cohesion, low coupling - exemplifies Structured Design principles


### `complex_pricing_logic`
- **File:** sample_ecommerce.py:109
- **Cohesion:** Sequential (Functional/Sequential)
- **Assessment:** High cohesion, low coupling - exemplifies Structured Design principles


### `validate_promo`
- **File:** sample_ecommerce.py:162
- **Cohesion:** Functional (Functional/Sequential)
- **Assessment:** High cohesion, low coupling - exemplifies Structured Design principles

---

## ⚠️  The Bad: Modules Needing Improvement

*These modules show design issues that should be addressed to improve maintainability.*


### 1. `handle_transaction`
- **File:** sample_ecommerce.py:17
- **Cohesion Level:** Logical

**Coupling Issues:**
- Parameter 'transaction_type' suggests control coupling (passing control information)

**Recommendations:**
⚠️  CRITICAL: Split this module - it combines unrelated operations
Consider breaking into separate, functionally cohesive modules
⚠️  Reduce coupling:
  - Parameter 'transaction_type' suggests control coupling (passing control information)


### 2. `initialize_system`
- **File:** sample_ecommerce.py:31
- **Cohesion Level:** Temporal

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 3. `process_order_steps`
- **File:** sample_ecommerce.py:44
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 4. `create_customer_profile`
- **File:** sample_ecommerce.py:61
- **Cohesion Level:** Procedural

**Coupling Issues:**
- High parameter count (14) - complex interface increases coupling

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function
⚠️  Reduce coupling:
  - High parameter count (14) - complex interface increases coupling
⚠️  Too many parameters - consider using a data structure or splitting the function


### 5. `process_user_order`
- **File:** sample_ecommerce.py:73
- **Cohesion Level:** Procedural

**Coupling Issues:**
- Uses global variables: CURRENT_USER, ORDER_COUNT - pathological coupling

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function
⚠️  Reduce coupling:
  - Uses global variables: CURRENT_USER, ORDER_COUNT - pathological coupling


### 6. `format_report`
- **File:** sample_ecommerce.py:84
- **Cohesion Level:** Procedural

**Coupling Issues:**
- Parameter 'format_flag' suggests control coupling (passing control information)
- Parameter 'include_details_flag' suggests control coupling (passing control information)
- Parameter 'sort_mode' suggests control coupling (passing control information)

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function
⚠️  Reduce coupling:
  - Parameter 'format_flag' suggests control coupling (passing control information)
  - Parameter 'include_details_flag' suggests control coupling (passing control information)
  - Parameter 'sort_mode' suggests control coupling (passing control information)


### 7. `process_payment`
- **File:** sample_ecommerce.py:142
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 8. `process_refund`
- **File:** sample_ecommerce.py:143
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 9. `process_adjustment`
- **File:** sample_ecommerce.py:144
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 10. `process_cancellation`
- **File:** sample_ecommerce.py:145
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 11. `load_config`
- **File:** sample_ecommerce.py:146
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 12. `connect_to_database`
- **File:** sample_ecommerce.py:147
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 13. `setup_api_client`
- **File:** sample_ecommerce.py:148
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 14. `configure_logging`
- **File:** sample_ecommerce.py:149
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function


### 15. `initialize_cache`
- **File:** sample_ecommerce.py:150
- **Cohesion Level:** Procedural

**Recommendations:**
⚠️  Consider refactoring to improve cohesion
Try to make each module perform a single, well-defined function

---

## 🚨 The Ugly: Critical Design Flaws

*These modules have serious design problems that significantly impact maintainability and should be refactored as soon as possible.*


### 1. `handle_transaction` - REQUIRES IMMEDIATE ATTENTION
- **File:** sample_ecommerce.py:17
- **Cohesion:** Logical (Score: 2/7) ⚠️  
- **Description Test:** ❌ Name contains 'and' - suggests multiple purposes (low cohesion)

**Complexity Metrics:**
- Lines of Code: 11
- Parameters: 2
- Cyclomatic Complexity: 5
- Max Nesting Depth: 4
- Function Calls: 4

**All Issues:**
- Parameter 'transaction_type' suggests control coupling (passing control information)

**🔧 How to Fix:**
⚠️  CRITICAL: Split this module - it combines unrelated operations
Consider breaking into separate, functionally cohesive modules
⚠️  Reduce coupling:
  - Parameter 'transaction_type' suggests control coupling (passing control information)

---

## 📋 Overall Recommendations

- Overall system shows low cohesion. Focus on splitting modules to achieve functional cohesion - each module should do ONE well-defined thing.

---

## 📚 Key Structured Design Principles

For reference, here are the core principles your code is being evaluated against:

### Cohesion Levels (Best to Worst)
1. **Functional** (Best) - Module performs one well-defined task
2. **Sequential** - Output of one element feeds next
3. **Communicational** - Elements operate on same data
4. **Procedural** - Elements follow specific sequence
5. **Temporal** - Elements executed at same time
6. **Logical** - Elements in same logical class, selected by flag
7. **Coincidental** (Worst) - Random grouping of elements

### Coupling Goals
- **Minimize interfaces** between modules
- **Use data coupling only** - pass only input/output data
- **Avoid control coupling** - don't pass flags that control behavior
- **Never use hybrid coupling** - don't modify other modules' code

### Design Mantras
> "Each module should do ONE thing and do it well."  
> "The goal is systems that are easy to understand, easy to modify, and easy to maintain."  
> "Design for humans, not just machines."

---

*Analysis performed by Structured Design Analyzer based on Constantine & Yourdon's principles.*
