# Chatper 4 Preliminary

## Toy Example

**Source Rust code**
```rust
fn main() {
    let bob = Box::new(1); 
}
```

**HIR**
Obtain the HIR of the source code 
```
cargo rustc -- -Z unpretty=hir-tree
```
```
Crate {
    owners: [
        ...
        Owner(
            OwnerInfo {
                nodes: OwnerNodes {
                    node: Some(
                        ParentedNode {
                            parent: 4294967040,
                            node: Item(
                                Item {
                                    ident: main#0,
                                    owner_id: DefId(0:3 ~ toy[5100]::main),
                                    kind: Fn(
                                        FnSig {
                                            header: FnHeader {
                                                unsafety: Normal,
                                                constness: NotConst,
                                                asyncness: NotAsync,
                                                abi: Rust,
                                            },
                                            decl: FnDecl {
                                                inputs: [],
                                                output: DefaultReturn(
                                                    src/main.rs:1:10: 1:10 (#0),
                                                ),
                                                c_variadic: false,
                                                implicit_self: None,
                                                lifetime_elision_allowed: false,
                                            },
                                            span: src/main.rs:1:1: 1:10 (#0),
                                        },
                                        Generics {
                                            params: [],
                                            predicates: [],
                                            has_where_clause_predicates: false,
                                            where_clause_span: src/main.rs:1:10: 1:10 (#0),
                                            span: src/main.rs:1:8: 1:8 (#0),
                                        },
                                        BodyId {
                                            hir_id: HirId(DefId(0:3 ~ toy[5100]::main).11),
                                        },
                                    ),
                                    span: src/main.rs:1:1: 3:2 (#0),
                                    vis_span: no-location (#0),
                                },
                            ),
                        },
                    ),

                    ...
                    bodies: {
                        11: Body {
                            params: [],
                            value: Expr {
                                hir_id: HirId(DefId(0:3 ~ toy[5100]::main).11),
                                kind: Block(
                                    Block {
                                        stmts: [
                                            Stmt {
                                                hir_id: HirId(DefId(0:3 ~ toy[5100]::main).1),
                                                kind: Local(
                                                    Local {
                                                        pat: Pat {
                                                            hir_id: HirId(DefId(0:3 ~ toy[5100]::main).9),
                                                            kind: Binding(
                                                                BindingAnnotation(
                                                                    No,
                                                                    Not,
                                                                ),
                                                                HirId(DefId(0:3 ~ toy[5100]::main).9),
                                                                bob#0,
                                                                None,
                                                            ),
                                                            span: src/main.rs:2:9: 2:12 (#0),
                                                            default_binding_modes: true,
                                                        },
                                                        ty: None,
                                                        init: Some(
                                                            Expr {
                                                                hir_id: HirId(DefId(0:3 ~ toy[5100]::main).2),
                                                                kind: Call(
                                                                    Expr {
                                                                        hir_id: HirId(DefId(0:3 ~ toy[5100]::main).3),
                                                                        kind: Path(
                                                                            TypeRelative(
                                                                                Ty {
                                                                                    hir_id: HirId(DefId(0:3 ~ toy[5100]::main).5),
                                                                                    kind: Path(
                                                                                        Resolved(
                                                                                            None,
                                                                                            Path {
                                                                                                span: src/main.rs:2:15: 2:18 (#0),
                                                                                                res: Def(
                                                                                                    Struct,
                                                                                                    DefId(5:276 ~ alloc[1281]::boxed::Box),
                                                                                                ),
                                                                                                segments: [
                                                                                                    PathSegment {
                                                                                                        ident: Box#0,
                                                                                                        hir_id: HirId(DefId(0:3 ~ toy[5100]::main).4),
                                                                                                        res: Def(
                                                                                                            Struct,
                                                                                                            DefId(5:276 ~ alloc[1281]::boxed::Box),
                                                                                                        ),
                                                                                                        args: None,
                                                                                                        infer_args: true,
                                                                                                    },
                                                                                                ],
                                                                                            },
                                                                                        ),
                                                                                    ),
                                                                                    span: src/main.rs:2:15: 2:18 (#0),
                                                                                },
                                                                                PathSegment {
                                                                                    ident: new#0,
                                                                                    hir_id: HirId(DefId(0:3 ~ toy[5100]::main).6),
                                                                                    res: Err,
                                                                                    args: None,
                                                                                    infer_args: true,
                                                                                },
                                                                            ),
                                                                        ),
                                                                        span: src/main.rs:2:15: 2:23 (#0),
                                                                    },
                                                                    [
                                                                        Expr {
                                                                            hir_id: HirId(DefId(0:3 ~ toy[5100]::main).7),
                                                                            kind: Lit(
                                                                                Spanned {
                                                                                    node: Int(
                                                                                        1,
                                                                                        Unsuffixed,
                                                                                    ),
                                                                                    span: src/main.rs:2:24: 2:25 (#0),
                                                                                },
                                                                            ),
                                                                            span: src/main.rs:2:24: 2:25 (#0),
                                                                        },
                                                                    ],
                                                                ),
                                                                span: src/main.rs:2:15: 2:26 (#0),
                                                            },
                                                        ),
                                                        els: None,
                                                        hir_id: HirId(DefId(0:3 ~ toy[5100]::main).8),
                                                        span: src/main.rs:2:5: 2:27 (#0),
                                                        source: Normal,
                                                    },
                                                ),
                                                span: src/main.rs:2:5: 2:27 (#0),
                                            },
                                        ],
                                        expr: None,
                                        hir_id: HirId(DefId(0:3 ~ toy[5100]::main).10),
                                        rules: DefaultBlock,
                                        span: src/main.rs:1:11: 3:2 (#0),
                                        targeted_by_break: false,
                                    },
                                    None,
                                ),
                                span: src/main.rs:1:11: 3:2 (#0),
                            },
                            generator_kind: None,
                        },
                    },
                    opt_hash_including_bodies: Some(
                        Fingerprint(
                            17038548455900965345,
                            6128119105717993704,
                        ),
                    ),
                },
                parenting: {},
                attrs: AttributeMap {
                    map: {},
                    opt_hash: Some(
                        Fingerprint(
                            17025902295854411478,
                            11375155654212205663,
                        ),
                    ),
                },
                trait_map: {
                    3: [],
                },
            },
        ),
    ],
    opt_hir_hash: Some(
        Fingerprint(
            13212131797653419263,
            9623007000143043823,
        ),
    ),
}

```


**MIR**
Obtain the MIR of the source code 
```
cargo rustc -- -Zunpretty=mir
```

```
fn main() -> () {
    let mut _0: ();
    let _1: std::boxed::Box<i32>;
    scope 1 {
        debug bob => _1;
    }

    bb0: {
        _1 = Box::<i32>::new(const 1_i32) -> [return: bb1, unwind continue];
    }

    bb1: {
        drop(_1) -> [return: bb2, unwind continue];
    }

    bb2: {
        return;
    }
}
```

## Compiler Internal

 - [**TyCtxt**](https://doc.rust-lang.org/nightly/nightly-rustc/rustc_middle/ty/struct.TyCtxt.html) is the central data structure of Rust compilers. We can obtain the hir or mir of a function based on the object.
```rust
let hir = tcx.hir();
let mir = optimized_mir(def_id); // def_id is of type DefId
```

### HIR
[HIR](https://rustc-dev-guide.rust-lang.org/hir.html)

 - [**DefId**](https://doc.rust-lang.org/nightly/nightly-rustc/rustc_span/def_id/struct.DefId.html): 
 - [**Local**](https://doc.rust-lang.org/nightly/nightly-rustc/rustc_middle/mir/struct.Local.html):
 - [**LocalDecl**](https://doc.rust-lang.org/nightly/nightly-rustc/rustc_middle/mir/struct.LocalDecl.html):

### MIR
[MIR](https://rustc-dev-guide.rust-lang.org/mir/index.html)
