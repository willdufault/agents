# AGENTS.md

## General

- **Keep all responses brief.** Every message, including thoughts and reasoning, should be direct and to the point. Use as few words as possible. No filler, no preamble, no summaries of what you just did.
  - Good: `Added null check to getUserById.`
  - Bad: `I've gone ahead and added a null check to the getUserById function to make sure we handle the case where the user doesn't exist. Let me know if you'd like any changes!`

- **Never use em dashes.** Use a comma, period, or rewrite the sentence instead.
  - Good: `This is fast, but not always accurate.`
  - Bad: `This is fast — but not always accurate.`

- **Never use emojis** in any response or communication.
  - Good: `Build complete.`
  - Bad: `Build complete! 🎉`

- **Only perform the task explicitly requested.** Do not fix unrelated issues, refactor surrounding code, or add unrequested features.
  - Good: *(asked to fix a bug in `saveUser`)* Fix only that bug.
  - Bad: *(asked to fix a bug in `saveUser`)* Also rename variables, reformat the file, and add logging.

## Code

- **Write simple, readable code.** Prefer clarity over cleverness or performance unless performance is the goal.
  - Good:
    ```python
    result = []
    for row in matrix:
        for value in row:
            result.append(value)
    ```
  - Bad:
    ```python
    result = [value for row in matrix for value in row]
    ```

- **Use comments sparingly.** Only comment to (1) add external context not obvious from the code, or (2) clarify genuinely complex logic. Do not comment obvious code.
  - Good:
    ```python
    # Offset by 1 because the API uses 1-based page indexing
    page = requested_page + 1
    ```
  - Bad:
    ```python
    # Add 1 to page
    page = requested_page + 1
    ```

- **Add a brief comment at the top of every source file** describing what the file does or represents.
  - Good:
    ```python
    # Handles authentication token generation and validation.
    ```
  - Bad: *(no top-of-file comment)*

- **Extract duplicate logic** into reusable variables, functions, or classes.
  - Good:
    ```python
    TAX_RATE = 0.08
    item_tax = price * TAX_RATE
    shipping_tax = shipping_cost * TAX_RATE
    ```
  - Bad:
    ```python
    item_tax = price * 0.08
    shipping_tax = shipping_cost * 0.08
    ```

- **Use guard clauses** to avoid deep nesting.
  - Good:
    ```python
    def process_order(order):
        if not order:
            return
        if not order.is_paid:
            return
        ship(order)
    ```
  - Bad:
    ```python
    def process_order(order):
        if order:
            if order.is_paid:
                ship(order)
    ```

- **Create intermediate variables** to break up complex expressions.
  - Good:
    ```python
    is_eligible = user.age >= 18 and user.has_verified_email
    has_credit = user.credit_score > 700
    if is_eligible and has_credit:
        ...
    ```
  - Bad:
    ```python
    if user.age >= 18 and user.has_verified_email and user.credit_score > 700:
        ...
    ```

- **Use unambiguous names** for all variables, functions, classes, files, and folders. Avoid abbreviations, single letters, or vague terms like `data`, `info`, `temp`, `obj`.
  - Good: `invoice_line_items`, `fetch_user_by_id()`, `UserAuthService`, `invoice_line_items.py`
  - Bad: `items`, `get_data()`, `Service`, `utils.py`
