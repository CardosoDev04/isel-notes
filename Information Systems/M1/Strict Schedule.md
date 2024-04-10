A strict schedule refers to a schedule on which no transaction T can read or write to a data item that was previously written by T' until T' commits or aborts it's changes.

Strict schedules ensure [[Recoverability]] and is easily recovered since, for example, the way to undo a write_item(X) is simply to restore said item to it's previous snapshot. (old_value or BFIM).