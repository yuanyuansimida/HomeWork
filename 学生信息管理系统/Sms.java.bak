package com.wsw.ch18;

import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Scanner;

public class Sms {
	List<Student> stus = new ArrayList<Student>();

	public Sms() {

	}

	// 保存学生的信息
	public void save(Student stu) {
		stus.add(stu);
	}

	// 查询学生

	public List<Student> findAll() {
		return stus;
	}

	// 通过id查询学生

	public Student findById(long id) {
		for (Student stu : stus) {
			if (stu.getId() == id) {
				return stu;
			}
		}
		return null;
	}

	// 通过id删除学生
	public void deletById(long id) {
		Iterator<Student> iter = stus.iterator();
		while (iter.hasNext()) {
			if (iter.next().getId() == id) {
				iter.remove();
			}
		}

	}

	// 更新学生信息
	public void update(Student newStu) {
		for (Student stu : stus) {
			if (stu.getId() == newStu.getId()) {
				stu.setName(newStu.getName());
				stu.setAge(newStu.getAge());
			}
		}
	}

	public void menu() {
		System.out.println("******学生信息管理系统******");
		System.out.println("1.查询学生信息");
		System.out.println("2.录入学生信息");
		System.out.println("3.删除学生信息");
		System.out.println("4.查看学生信息");
		System.out.println("5.更改学生信息");
		System.out.println("help.帮助");
		System.out.println("exit.退出");
		System.out.println("***********************");
	}

	public static void main(String[] args) {
		Sms sms = new Sms();
		Scanner sc = new Scanner(System.in);
		sms.menu();
		while (true) {
			System.out.print("请输入指令：");
			String option = sc.nextLine();
			System.out.println("用户输入的指令：" + option);
			switch (option) {
			case "1": {// 查询学生信息
				System.out.println("以下是所有学生的信息:");
				// 调用findAll方法查询学生
				List<Student> arr = sms.findAll();
				for (Student stu : arr) {
					System.out.println(stu);
				}
				System.out.println("总共 " + sms.stus.size() + "个学生");
				break;
			}
			case "2": {// 录入学生信息
				while (true) {
					System.out.println("请输入学生信息【id#name#age】或输入【break】");
					String stustr = sc.nextLine();
					if (stustr.equals("break")) {
						break;
					}
					String[] stuArr = stustr.split("#");
					long id = Long.parseLong(stuArr[0]);
					String name = stuArr[1];
					int age = Integer.parseInt(stuArr[2]);
					Student stu = new Student(id, name, age);
					sms.save(stu);
					System.out.println("录入成功！");
				}
				break;
			}
			case "3": {// 删除学生信息
				while (true) {
					System.out.println("请输入要删除学生的【id】或者【break】返回");
					String idStr = sc.nextLine();
					if (idStr.equals("brenk")) {
						break;
					}
					long id = Long.parseLong(idStr);
					Student stu = sms.findById(id);
					if (stu == null) {
						System.out.println("该学生不存在");
						continue;
					}
					// 删除学生
					sms.deletById(id);
					System.out.println("删除成功！");

				}
				break;
			}
			case "4": {// 查看学生信息
				while (true) {
					System.out.println("请输入要查找学生的【id】或者【break】返回");
					String idStr = sc.nextLine();
					if (idStr.equals("break")) {
						break;
					}
					long id = Long.parseLong(idStr);
					Student stu = sms.findById(id);
					if (stu == null) {
						System.out.println("该学生不存在");
						continue;
					}
					System.out.println(stu);
				}
				break;
			}
			case "5": {
				while (true) {
					System.out.println("请输入要修改学生的【id】或者输入【break】返回主目录");
					String idStr = sc.nextLine();
					if (idStr.equals("break")) {
						break;
					}
					// 将字符串id转换为长整型
					long id = Long.parseLong(idStr);
					Student stu = sms.findById(id);
					if (stu == null) {
						System.out.println("您要修改的学生信息不存在！");
						continue;
					}

					System.out.println("您要修改的学生信息为：" + stu);
					System.out.println("请输入该学生的新信息【name#age】");
					String stuStr = sc.nextLine();
					String[] stuArr = stuStr.split("#");
					String name = stuArr[0];
					int age = Integer.parseInt(stuArr[1]);
					Student newStu = new Student(id, name, age);
					sms.update(newStu);
					System.out.println("修改成功");
				}
				break;
			}
			case "help": {
				sms.menu();
				break;
			}
			case "exit": {
				System.out.println("退出学生管理系统,欢迎您下次使用");
				System.exit(0);
				break;
			}
			default:
				System.out.println("用户输入指令有误！");
				break;

			}
		}
	}
}
