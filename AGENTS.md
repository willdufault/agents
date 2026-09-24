# AGENTS.md

## General

- **Be brief.** All responses must be direct and to the point. No filler, no preamble, no summaries.
  - Good: `Added null check to getUserById.`
  - Bad: `I've gone ahead and added a null check to the getUserById function to make sure we handle the case where the user doesn't exist. Let me know if you'd like any changes!`

- **Never use em dashes.** Use a comma or period instead.
  - Good: `This is fast, but not always accurate.`
  - Bad: `This is fast — but not always accurate.`

- **Never use emojis.**
  - Good: `Build complete.`
  - Bad: `Build complete! 🎉`

- **Only perform the task requested.** Do not fix unrelated issues or add unrequested changes.
  - Good: *(asked to fix a bug in `saveUser`)* Fix only that bug.
  - Bad: *(asked to fix a bug in `saveUser`)* Also rename variables, reformat the file, and add logging.

## Code

- **Write simple, readable code.** Prefer clarity over cleverness or performance.
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

- **Use comments sparingly.** Only to (1) add external context, or (2) clarify genuinely complex logic.
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

- **Add a comment at the top of every source file.** Describe what it does.
  - Good:
    ```python
    # Handles authentication token generation and validation.
    ```
  - Bad: *(no top-of-file comment)*

- **Extract duplicate logic.** Pull it into reusable variables, functions, or classes.
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

- **Use guard clauses.** Avoid deep nesting.
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

- **Create intermediate variables.** Break up complex expressions.
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

- **Use unambiguous names.** Applies to variables, functions, classes, files, and folders. Avoid `data`, `info`, `temp`, `obj`, single letters, and abbreviations.
  - Good: `invoice_line_items`, `fetch_user_by_id()`, `UserAuthService`
  - Bad: `items`, `get_data()`, `Service`

- **One word, one meaning.** Use the same term for the same concept throughout the codebase.
  - Good: `delete_user()`, `delete_account()` use `delete_` consistently for destructive operations.
  - Bad: `delete_user()` in one place, `remove_account()` in another for the same type of operation.

- **Follow existing patterns in the codebase.** Reuse existing abstractions rather than creating new ones.
  - Good: The codebase has `handle_error()`, so you call that.
  - Bad: The codebase has `handle_error()`, but you write a new `log_and_raise()` that does the same thing.

- **Use whitespace to separate logical blocks.** Add blank lines between distinct steps.
  - Good:
    ```python
    user = get_user(user_id)
    account = get_account(user.account_id)

    if not account.is_active:
        return

    send_welcome_email(user, account)
    log_login(user)
    ```
  - Bad:
    ```python
    user = get_user(user_id)
    account = get_account(user.account_id)
    if not account.is_active:
        return
    send_welcome_email(user, account)
    log_login(user)
    ```

- **Group logically similar code together.** Keep related operations together, unrelated operations separate.
  - Good:
    ```python
    user = get_user(user_id)
    account = get_account(user.account_id)
    permissions = get_permissions(user)

    if not account.is_active:
        return
    apply_permissions(user, permissions)
    ```
  - Bad:
    ```python
    user = get_user(user_id)
    if not user:
        return
    permissions = get_permissions(user)
    account = get_account(user.account_id)
    if not account.is_active:
        return
    apply_permissions(user, permissions)
    ```
