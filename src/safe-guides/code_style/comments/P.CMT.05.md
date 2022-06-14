# P.CMT.05 Use `FIXME` and `TODO` in comments to help with task collaboration

**[Description]**

Collaboration can be facilitated by turning on `FIXME` and `TODO` in the comments.

Note: This entry is not suitable for use with `rustfmt` related configuration items `report_fixme` and `report_todo`, which have been removed in `rustfmt` v2.0.

**[Good Case]**

```rust
// Good
// TODO(calebcartwright): consider enabling box_patterns feature gate
fn annotation_type_for_level(level: Level) -> AnnotationType {
    match level {
        Level::Bug | Level::Fatal | Level::Error => AnnotationType::Error,
        Level::Warning => AnnotationType::Warning,
        Level::Note => AnnotationType::Note,
        Level::Help => AnnotationType::Help,
        // FIXME(#59346): Not sure how to map these two levels
        Level::Cancelled | Level::FailureNote => AnnotationType::Error,
        Level::Allow => panic!("Should not call with Allow"),
    }
}
```
