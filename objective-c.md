---
title: "Let's Learn: Objective-C"
created_at: 2014-02-22 10:36:51 +0400
kind: cheatsheet
keywords: [apple, xcode, code, cheatsheet]
---

## XCode

`Alt+LMB` - display quick help inline  


## Objective-C Basics (based on [this](http://www.raywenderlich.com/4872/objective-c-cheat-sheet-and-quick-reference))

### Class Header - Interface (.h)

```Objective-c
#import "AnyHeaderFile.h"

@interface ClassName : NSObject

// declare public properties
// attribute1&2 can be strong, weak, assign, copy, nonatomic, readwrite, readonly
// properties auto. declare "type _propertyName" private instance variable and
// getter "- (type)propertyName;" and setter "- (void)setPropertyName:(type)name;"
@property (attribute1, attribute2) type propertyName;

// declare public methods
+ (type)classMethod;
- (type)doIt;
- (type)doItWithA:(type)a;
- (type)doItWithA:(type)a andB:(type)b;

- (id)initWithParam:(type)param;

@end
```

### Class Implementation (.m)

```Objective-C
#import "YourClassName.h"

@interface ClassName ()

// define private properties and methods

@end

@implementation ClassName

// implement properties
@synthesize propertyName;

// declare private instance variables
type myVariable;

// implement methods

// class method
+ (type)classMethod {
	// ...
}

// instance method
- (type)doItWithA:(type)a andB:(type)b {
	// self = this, must be used
	NSLog(@"items ", [self.items count]);

	// create an object
	ClassName *myObject = [[ClassName alloc] init];

	// call a method
	[myObject doIt];
	[myObject doItWithA:a];
	[myObject doItWithA:a andB:b];

	// using properties
	[myObject setPropertyName:a]; // or
	myObject.propertyName = a;

	a = [myObject propertyName]; // or
	a = myObject.propertyName;

	return something;
}

// custom initializer example (default method name is "init")
- (id)initWithParam:(type) param {
	if ((self = [super init])) {
		_propertyName = param;
	}

	return self;
}

// destructor
- (void) dealloc {
	[myObject release];
	self.otherObject = nil; // nil can be set instead of calling release

	[super dealloc];
}

@end
```

### Foundation Classes

```Objective-C
NSString *string = @"something cool";
NSString *string2 = [NSString stringWithFormat:@"%d %@", 1, @"string"];
NSString *string3 = [NSString stringWithCString:"some C string" encoding:NSUTF8StringEncoding];

NSNumber *intValue = @32;
NSNumber *floatValue = @3.2f;
NSNumber *doubleValue = @3.1412;
NSNumber *boolValue = @YES;
NSNumber *charValue = @'V';

NSArray *myArray = [NSArray arrayWithObjects:string, intValue, charValue, nil]; // MUST end with nil!
NSArray *array2 = @[firstObject, secondObject, thirdObject]; // shorthand, NO nil at end
NSUInteger numItems = [someArray count];
if ([someArray containsObject:string1]) { ... }
NSLog(@"First item: %@", [someArray objectAtIndex:0]);
NSArray *sorted = [someArray sortedArrayUsingSelector:@selector(compare:)];

NSMutableString *mutable = [NSMutableString stringWithString:@"Hello"];
[string appendString:@" World!"];

NSMutableArray *mutableArray = [NSMutableArray array];
[mutableArray addObject:@"alpha"];
[mutableArray replaceObjectAtIndex:0 withObject:@"beta"];
[mutableArray sortUsingSelector:@selector(caseInsensitiveCompare:)];

// a set contains every object instance once
NSSet *mySet = [NSSet setWithObjects:@"Hello", @42, nil];

NSDictionary *dict = [NSDictionary dictionaryWithObjectsAndKeys:string1, @"something", @42, @"fourtytwo", nil] // key-value pairs, nil terminated
NSDictionary *dict2 = @{@42, @"magic number", @"name", @"attila"}; // shorthand, NO nil at end
NSNumber *num = [dict objectForKey:@"something"];
NSNumber *num2 = dict[@"something"]; // shorthand

NSMutableDictionary *mutableDict = [NSMutableDictionary dictionary];
[mutableDict setObject:@"magic number" forKey:@42];
[mutableDict removeObjectForKey:@42];

// represent nil in collections with NSNull, NOT nil!
NSArray *array = @[ @"hello", @42, [NSNull null] ];
for (id object in array) {
	if (object == [NSNull null])
		NSLog(@"Found a null object");
}

// Logging
NSLog(@"myObject is %@", myObject);
```

### Memory Management

Objects are *alloc*ated (or you can *copy* them), then maybe *retain*ed, then have to be *release*d or *autorelease*d for every alloc and retain. 


### UI-Specific

```Objective-C
// UI elements (senders) can perform IBActions
- (IBAction)restoreDefaults:(id)sender;

// IBOutlets reference objects in the UI
@property (weak, nonatomic) IBOutlet UITextField *textField;
```