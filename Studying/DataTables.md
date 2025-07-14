# Step #1: Prepare Data
```typescript
type Payment = {
	id: string;
	amount: number;
	status: 'Pending' | 'Processing' | 'Success' | 'Failed';
	email: string;
};

const data: Payment[] = [
	{ id: '1', amount: 100, status: 'Success', email: 'a@example.com' },
	// more rows...
];
```



---
