## 基础改键

caps → right_shift

## 高级改键

### Basic move

Can move in vim、vscode、finder without change ang conf

Please notice that in vscode `option + up/down` will swap lines

You can cancel `"optional": ["any"]` in `w/s`

```json
{
    "from": {
        "key_code": "w",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["any"]
        }
    },
    "to": [{
		"key_code": "up_arrow"
	}],
    "type": "basic"
},
{
    "from": {
        "key_code": "s",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["any"]
        }
    },
    "to": [{
		"key_code": "down_arrow"
	}],
    "type": "basic"
},
{
    "from": {
        "key_code": "a",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["option"]
        }
    },
    "to": [{
		"key_code": "left_arrow"
    }],
    "type": "basic"
},
{
    "from": {
        "key_code": "d",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["option"]
        }
    },
    "to": [{
		"key_code": "right_arrow"
	}],
    "type": "basic"
}
```

### Change for Finder

To enter and quit easily

```json
{
	"from": {
		"key_code": "q",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{
		"key_code": "up_arrow",
		"modifiers": "command"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "e",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{
		"key_code": "o",
		"modifiers": "command"
	}],
	"type": "basic"
}
```

### Change for Edit

```json
{
	"from": {
		"key_code": "delete_or_backspace",
		"modifiers": {
			"mandatory": ["right_shift"],
			"optional": ["any"]
		}
	},
	"to": [{
		"key_code": "delete_or_backspace"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "period",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{"key_code": "period"}],
	"type": "basic"
}
```

### Change for window hide

```json
{
	"from": {
		"key_code": "m",
		"modifiers": {"mandatory": ["command"]}
	},
	"to": [{
		"key_code": "h",
		"modifiers": "command"
	}],
	"type": "basic"
}
```

### 完整代码

```json
{
    "from": {
        "key_code": "w",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["any"]
        }
    },
    "to": [{
		"key_code": "up_arrow"
	}],
    "type": "basic"
},
{
    "from": {
        "key_code": "s",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["any"]
        }
    },
    "to": [{
		"key_code": "down_arrow"
	}],
    "type": "basic"
},
{
    "from": {
        "key_code": "a",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["option", "control"]
        }
    },
    "to": [{
		"key_code": "left_arrow"
    }],
    "type": "basic"
},
{
    "from": {
        "key_code": "d",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["option", "control"]
        }
    },
    "to": [{
		"key_code": "right_arrow"
	}],
    "type": "basic"
},
{
	"from": {
		"key_code": "q",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{
		"key_code": "up_arrow",
		"modifiers": "command"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "e",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{
		"key_code": "o",
		"modifiers": "command"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "delete_or_backspace",
		"modifiers": {
			"mandatory": ["right_shift"],
			"optional": ["any"]
		}
	},
	"to": [{
		"key_code": "delete_or_backspace"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "period",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{"key_code": "period"}],
	"type": "basic"
},
{
	"from": {
		"key_code": "m",
		"modifiers": {"mandatory": ["command"]}
	},
	"to": [{
		"key_code": "h",
		"modifiers": "command"
	}],
	"type": "basic"
}
```


## Mandatory 和 Optional 的解释

Mandatory: 写在 Mandatory 中的按键必须按住, 否则无法生效

Optional: 写在 Optional 中的按键是修饰映射后的结果, 比如 `Mandatory (shift) + w` 为 `up`, 则 `Optional (cmd)` 是修饰 `up` 键的, 最终结果为 `cmd + up`, 否则将输入 `cmd + shift + w`, 即触发系统快捷键

## 映射细节问题

w、s 的 optional 

不添加 cmd , 会触发系统的 cmd shift w 快捷键, 也就是可以触发 cmd shift a、d 进入 App

添加 command, 则容易触发 cmd + up, 会跳到开头, 并且无法触发系统的 cmd shift a、d

同时, 我希望按住 space 进行修饰选中, 取代 shift 位置

添加 right_command, 选择行时容易按住 cmd, 但实际变成了选中到开头, 只能单独添加映射, 这边就必须都写到 `Mandatory` 里

```json
// 写法一, 左手仅按住 cmd + shift + w 就会选中, 感觉还是选中时右手再按住 shift 较好, 且会触发问题
// right_command + right_shift + w → shift + up
// right_command + right_shift + s  → shift + down

{
    "from": {
        "key_code": "w",
        "modifiers": {
            "mandatory": ["right_shift","command"]
        }
    },
    "to": [{
        "key_code": "up_arrow",
        "modifiers": "shift"
    }],
    "type": "basic"
},
{
    "from": {
        "key_code": "s",
        "modifiers": {
            "mandatory": ["right_shift","right_command"]
        }
    },
    "to": [{
        "key_code": "down_arrow",
        "modifiers": "shift"
    }],
    "type": "basic"
}
```

```json
// 写法二, 好一点, 右手按住 shift 才进入选中状态
// 重复使得按住 cmd 移动更快
{
    "from": {
        "key_code": "w",
        "modifiers": {
            "mandatory": ["right_shift","command"],
            "optional": ["option","control","right_shift"]
        }
    },
    "to": [
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"}
    ],
    "type": "basic"
},
{
    "from": {
        "key_code": "s",
        "modifiers": {
            "mandatory": ["right_shift","command"],
            "optional": ["option","control","right_shift"]
        }
    },
    "to": [
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"}
    ],
    "type": "basic"
}
```



## 这才是完整

```json
{
    "from": {
        "key_code": "w",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["any"]
        }
    },
    "to": [{
		"key_code": "up_arrow"
	}],
    "type": "basic"
},
{
    "from": {
        "key_code": "s",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["any"]
        }
    },
    "to": [{
		"key_code": "down_arrow"
	}],
    "type": "basic"
},
{
    "from": {
        "key_code": "w",
        "modifiers": {
            "mandatory": ["right_shift","command"],
            "optional": ["option","control","right_shift"]
        }
    },
    "to": [
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"},
        {"key_code": "up_arrow"}
    ],
    "type": "basic"
},
{
    "from": {
        "key_code": "s",
        "modifiers": {
            "mandatory": ["right_shift","command"],
            "optional": ["option","control","right_shift"]
        }
    },
    "to": [
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"},
        {"key_code": "down_arrow"}
    ],
    "type": "basic"
},
{
    "from": {
        "key_code": "a",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["option", "control"]
        }
    },
    "to": [{
		"key_code": "left_arrow"
    }],
    "type": "basic"
},
{
    "from": {
        "key_code": "d",
        "modifiers": {
            "mandatory": ["right_shift"],
            "optional": ["option", "control"]
        }
    },
    "to": [{
		"key_code": "right_arrow"
	}],
    "type": "basic"
},
{
	"from": {
		"key_code": "q",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{
		"key_code": "up_arrow",
		"modifiers": "command"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "e",
		"modifiers": {"mandatory": ["right_shift"]}
	},
	"to": [{
		"key_code": "o",
		"modifiers": "command"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "delete_or_backspace",
		"modifiers": {
			"mandatory": ["right_shift"],
			"optional": ["any"]
		}
	},
	"to": [{
		"key_code": "delete_or_backspace"
	}],
	"type": "basic"
},
{
	"from": {
		"key_code": "m",
		"modifiers": {"mandatory": ["command"]}
	},
	"to": [{
		"key_code": "h",
		"modifiers": "command"
	}],
	"type": "basic"
}
```